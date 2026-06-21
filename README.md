# the TEAM

A personal AI advisory council — 25 named advisor personas plus **CATYOUSHA**, a chief-of-staff who runs the room. Built in the open [Agent Skills](https://github.com/anthropics/skills) format (a `SKILL.md` plus on-demand reference files), with a parallel Kiro steering-file variant.

The point of the skill is **honest, in-character orchestration**: on any decision, the right voices speak, real disagreement surfaces, and the session ends in a clear call or action — not a wall of agreeable voices nodding along. It's product-agnostic: it works on whatever product, project, or personal decision is in front of you.

---

## How you use it

Two paths, by far the most common first:

1. **Call a member by name** (the primary path) — `YASSER, cheapest way to run this Postgres?` Gets a direct, in-character, in-lane answer. No panel. If it's outside their lane, they hand off instead of bluffing.
2. **Fire a trigger** (less often, for structured sessions) — `DANGER — should we add Azure support next quarter?` Convenes a roundtable that argues and closes with a verdict.

Worked examples of both live in `references/examples.md`.

## The roster at a glance

| Group | Members |
|---|---|
| **Assistant** | CATYOUSHA (runs every session) |
| **Build & Secure** | JOOBOO (CTO/full-stack), MOTASEM (cloud architect), YASSER (AWS + on-prem/hybrid), NAJI (DB architect + DBA), RAID (security), YAZEED (AI), ASEEL (QA), MOAMEN (product), AMANAK (program mgmt) |
| **Market & Money** | RAMOS (strategy/partnerships), RAMI (sales), MAHER (marketing), MURAD (CFO), ABE (company capital/fundraising), ANOOS (personal wealth), AHMAD (legal), FERAS (customer success) |
| **Craft & Comms** | SAVEE (creative direction), LAMA (technical writing) |
| **Wisdom & Self** | ARWA (Islamic/ethics lens), MOHAMMAD (psychology), TAMER (gut-check) |
| **Stress-Test (cross-cutting)** | ZOBRONSIKI (contrarian), ABU SEINI (first-principles), JAABARI (outsider) — seat by default on DANGER/CRASH/ATTACK |

Full character cards: `references/roster.md`. The deeper per-member Role/Task/Context/Reasoning/Stop-Conditions/Output layer: `references/pillars.md`.

## Triggers

| Trigger | For |
|---|---|
| `RULE` | a reminder of how the team works |
| `DANGER` | options + tradeoffs laid out; you decide |
| `THINK` | the team converges to one recommendation |
| `DECIDE` | a fast either/or call |
| `PLAN` | turn a decision into owned steps |
| `CRASH` | pre-mortem a chosen path |
| `ATTACK` | devil's-advocate a position you hold |
| `RESEARCH` | ground a topic in current, sourced facts before opinions |
| `RANK` | regular pulse on the team and what matters today |
| `MEETING` | credit a past call that proved right |
| `RECOMMENDATION` | flag a capability gap, propose a new member |

Full specs: `references/triggers.md`.

---

## Install — per tool

This repo ships **two variants**. Pick by tool.

### Native Agent Skills tools → use the repo root (`SKILL.md` + `references/`)

| Tool | Where it goes |
|---|---|
| **Claude.ai / Claude app** | Settings → Capabilities → Skills → upload (zip the root: `SKILL.md` + `references/`) |
| **Claude Code** | copy to `~/.claude/skills/the-team/` (personal) or `.claude/skills/the-team/` (project) |
| **Cursor** | copy to `.agents/skills/the-team/` (cross-client convention) |
| **VS Code (+ Copilot) / Codex** | via the Codex/Copilot skills path, same files |
| **Antigravity** | native Agent Skills support — same files |
| **Windsurf, Aider, OpenCode, Gemini CLI, …** | their skills dir, same files |

> Cross-client tip: `.agents/skills/` is the convention the most tools watch; some also scan `.claude/skills/`. If you want one folder picked up everywhere, use `.agents/skills/the-team/`.

### Kiro → use `kiro/.kiro/steering/`

Kiro doesn't load `SKILL.md` the same way — it uses **steering files**. Copy the contents of `kiro/.kiro/steering/` into your Kiro config:

- User-level (all projects): `~/.kiro/settings/steering/` → or merge into `~/.kiro/steering/`
- Workspace-only: `<project>/.kiro/steering/`

The files are `inclusion: manual`, so they don't burn context by default — pull one in with `#the-team` (or a trigger word once referenced). **Don't** load the Agent-Skills variant into Kiro; use this one.

---

## Repo structure

```
the-team/
├── README.md              ← this file
├── .gitignore
├── SKILL.md               ← the skill (Agent Skills format) — index, always loaded
├── references/            ← loaded on demand, never all at once
│   ├── roster.md          ← character cards (read when convening anyone)
│   ├── examples.md        ← worked sessions (read on first run in a new chat/tool)
│   ├── pillars.md         ← per-member Role/Task/Context/Reasoning/Stop/Output
│   ├── triggers.md        ← full spec for each trigger
│   └── research.md        ← research protocol + NotebookLM MCP setup (Claude & Kiro)
└── kiro/
    └── .kiro/steering/    ← the same skill, as Kiro manual-inclusion steering files
```

The lazy-load design is deliberate: `SKILL.md` stays thin and the reference files load only when actually needed, so sessions stay fast and cheap regardless of how big the roster gets.

---

## Caveats (read once)

- **Quality is model-dependent.** The format travels everywhere, but the skill leans on the host model's ability to hold 25 personas and run a real roundtable. It's sharpest on a strong frontier model and flatter on a weak one — same files, different room.
- **NotebookLM integration is third-party.** The setup in `references/research.md` uses community-maintained MCP bridges (not Google/Anthropic products) that drive a real Chrome session. Review the repo before granting Google-account access, and never commit the resulting auth — `.gitignore` already blocks the obvious secret paths.
- **headroom is optional and local.** It's referenced as a token-economy pattern and for wrapping Claude Code / Kiro CLI sessions. It's not used or required by the skill itself; it's a separate local install if you want it.

## A note on what this is

This is a personal council, not a marketplace product. It's tuned to one person's context and judgment. Triggers fire less often than direct name-calls; the team's value is the friction, not the headcount. The members evolve through use — `RANK` and `MEETING` are the growth log.
