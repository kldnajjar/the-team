# Research protocol & performance notes

Read this when a topic needs grounding in current reality, or when setting up the team's research tooling outside this chat (Claude Code / Kiro).

## The research protocol (used by `RESEARCH`, and silently by any lead before a market/competitor/regulation/pricing claim)

1. **Don't answer fast-moving facts from memory.** Competitor features, pricing, regulatory status, headcount, funding stage, "is X still the market leader" — these move. If it could have changed since training, it gets checked, not asserted.
2. **Search before opining.** Pull current sources (web search; NotebookLM if connected — see below) before any member states a market fact as fact.
3. **Tag every claim.** *Verified* = sourced just now. *Inferred* = the team's reasoned best guess, clearly labeled as such. Never blend the two without saying which is which.
4. **No fake "verified" tags.** If web search or NotebookLM isn't available in the current environment (e.g. a no-tools Kiro context, or the MCP isn't connected), a member must NOT tag anything *verified* — say "couldn't verify here, this is my best read" and tag it *inferred*. A confident verified-looking claim standing on no actual lookup is the one integrity failure that breaks trust in the whole team.
5. **Minimum viable research.** One or two sharp searches that answer the actual question beat ten generic ones. Stop once the question is answered.
6. **Surface conflicts, don't average them.** If sources disagree, say so — don't quietly pick one.

This is what makes a `DANGER` or `THINK` on a market question worth more than a confident guess: the team's edge is real information, not vocabulary.

## Performance & token discipline

The team's own design follows the same compression logic worth applying everywhere else Khaled runs AI agents:

- **Lazy-load, don't pre-load.** SKILL.md stays thin; roster, triggers, and this file load only when actually needed (see "Load only what you need" in SKILL.md). The same principle — compress/defer what the model doesn't need yet, keep originals retrievable — is what tools like [headroom](https://github.com/chopratejas/headroom) do for tool outputs, logs, and RAG chunks in coding-agent sessions (60–95% token reduction, reversible). If Khaled is running the TEAM inside **Claude Code** or **Kiro CLI** rather than claude.ai chat — sessions with heavy tool output (file reads, command results, search dumps) — wrapping that session is worth it:
  ```
  pip install "headroom-ai[all]"
  headroom wrap claude     # or: headroom mcp install
  ```
  Not relevant inside claude.ai chat itself — there's no local process to wrap there. Use it for the CLI tools.
- **Terse by default.** Every member's contribution is a few tight sentences. Don't restate context Khaled already gave. Expand only on request.
- **Match ceremony to stakes.** A DECIDE is three lines. Don't run DANGER-level theater on a question that's actually small — see "When NOT to convene the team" in SKILL.md.

## Connecting NotebookLM as a research source (Claude Desktop / Claude Code / Kiro)

This lets any member — most often CATYOUSHA, MOAMEN, or RAMOUS during a `RESEARCH` trigger — query Khaled's own NotebookLM notebooks (deep research on Archmate/Aqdee competitors, market reports, KSA/EU regulation sources, etc.) without leaving the conversation. This is a third-party, community-maintained bridge — not a Google or Anthropic product — so review the repo before granting it browser access to a Google account.

**Recommended option — [`PleasePrompto/notebooklm-mcp`](https://github.com/PleasePrompto/notebooklm-mcp).** It's a standard MCP server (stdio or Streamable-HTTP) that drives a real Chrome session for NotebookLM, which means the *same config block* works in Claude and Kiro without tool-specific glue.

**1. Install:**
```
git clone https://github.com/PleasePrompto/notebooklm-mcp
cd notebooklm-mcp
npm install
npm run build
```
This produces `dist/index.js`. (Node.js ≥18 and a real Chrome install are required; WSL2 if on Windows.)

**2. First-run auth:** the server opens a real Chrome window for a one-time Google sign-in to whichever account owns the target notebooks; the session persists after that. Use a separate Chrome profile (`--account work` / `--account personal`) if Khaled's CloudVests and personal Google accounts need to stay separate.

**3. Add to Claude Code:**
```
claude mcp add notebooklm -- node /absolute/path/to/notebooklm-mcp/dist/index.js
```

**4. Add to Claude Desktop** — edit `claude_desktop_config.json` (macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`):
```json
{
  "mcpServers": {
    "notebooklm": {
      "command": "node",
      "args": ["/absolute/path/to/notebooklm-mcp/dist/index.js"]
    }
  }
}
```

**5. Add to Kiro** — same JSON shape, dropped into Kiro's own MCP config (Kiro uses the identical `mcpServers` schema: `command` / `args` / `env` / `disabled` / `autoApprove`):
- User-level (all projects): `~/.kiro/settings/mcp.json`
- Workspace-only: `<project>/.kiro/settings/mcp.json`
```json
{
  "mcpServers": {
    "notebooklm": {
      "command": "node",
      "args": ["/absolute/path/to/notebooklm-mcp/dist/index.js"],
      "disabled": false,
      "autoApprove": []
    }
  }
}
```
Restart Kiro (or run `/mcp` in Kiro CLI) to confirm it loaded.

**Alternative — [`jacob-bd/notebooklm-mcp-cli`](https://github.com/jacob-bd/notebooklm-mcp-cli).** Trades the manual JSON for a setup command per tool (`nlm setup add claude-code`, `nlm setup add claude-desktop`, a one-click `.mcpb` extension for Claude Desktop, `nlm doctor` to diagnose). It doesn't list Kiro as a named target, but `nlm setup add json` prints the same standard config block above — paste that into Kiro's `mcp.json` the same way. Worth using if Khaled wants the CLI's bundled "skill install" helper rather than wiring the config by hand.

**Once connected**, point a member at it directly rather than re-explaining the research goal each time, e.g.: *"RAMOUS, pull the competitor-pricing notebook on Cloudchipr and LensGPT before we run DANGER on the FinOps tier."* Tag whatever comes back as *verified* per the protocol above.
