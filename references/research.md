# Research protocol

Read this when a topic needs grounding in current facts, or when setting up research tooling (Claude Code, Claude Desktop, Kiro).

## The protocol

Used by `RESEARCH`, and silently by any lead before stating a market, competitor, pricing or regulation claim.

1. **Don't answer fast-moving facts from memory.** Competitor features, pricing, regulatory status, funding, service availability by region: if it could have changed since training, check it.
2. **Search before opining.** Web search, plus NotebookLM if connected (below).
3. **Tag every claim.** *Verified* = sourced just now, with the source named. *Inferred* = the team's reasoned best guess, labelled as such.
4. **No fake "verified".** If no search tool is available, say "couldn't verify here" and tag it *inferred*. A verified-looking claim with no lookup behind it is the one failure that breaks trust in the whole team.
5. **Minimum viable research.** One or two sharp searches beat ten generic ones. Stop once the question is answered.
6. **Surface conflicts, don't average them.** If sources disagree, say so.

## Token discipline

- **Lazy-load.** SKILL.md stays thin; references load only when needed.
- **Terse by default.** No restating context Khaled already gave.
- **Match ceremony to stakes.** Don't run `DANGER` on a `DECIDE`-sized question.
- **Parallel mode costs more.** Each subagent re-reads the brief. Use it for decisions worth the spend (see `parallel-mode.md`).

## Optional: NotebookLM as a research source

Lets CATYOUSHA or RAMOUS query Khaled's own NotebookLM notebooks (competitor deep-dives, KSA/EU regulation sources, market reports) during `RESEARCH`.

> This is a **third-party, community-maintained** bridge, not a Google or Anthropic product. It drives a real Chrome session signed in to a Google account. Review the code before installing, and never commit the auth tokens it creates.

**Option A: [`PleasePrompto/notebooklm-mcp`](https://github.com/PleasePrompto/notebooklm-mcp)** (standard MCP server; the same config works in Claude and Kiro)

```bash
git clone https://github.com/PleasePrompto/notebooklm-mcp
cd notebooklm-mcp && npm install && npm run build   # Node ≥18 + Chrome
```

First run opens Chrome for a one-time Google sign-in. Use separate profiles if work and personal accounts must stay apart.

Claude Code:
```bash
claude mcp add notebooklm -- node /absolute/path/to/notebooklm-mcp/dist/index.js
```

Claude Desktop (`~/Library/Application Support/Claude/claude_desktop_config.json`) and Kiro (`~/.kiro/settings/mcp.json` or `<project>/.kiro/settings/mcp.json`):
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

**Option B: [`jacob-bd/notebooklm-mcp-cli`](https://github.com/jacob-bd/notebooklm-mcp-cli)** gives you setup commands instead of hand-written JSON (`nlm setup add claude-code`, `nlm setup add claude-desktop`, `nlm doctor`). For Kiro, `nlm setup add json` prints the same block as above.

Once connected, point a member at a notebook directly: *"RAMOUS, pull the competitor-pricing notebook before we run DANGER on the enterprise tier."* Results are tagged *verified*, with the notebook named as the source.
