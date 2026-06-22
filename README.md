# the TEAM

A personal AI advisory council — 25 named advisor personas plus **CATYOUSHA**, the chief of staff who runs the room.

Built in the [Agent Skills](https://github.com/anthropics/skills) format (`SKILL.md` + on-demand reference files), with a dedicated Kiro variant. Product-agnostic: works on whatever product, project, company, or personal decision is in front of you.

The point isn't headcount. It's **honest orchestration** — the right voices speak, real disagreement surfaces, and every session ends in a clear call or concrete action. Not a wall of agreeable voices nodding along.

---

## The Roster

| Group | Members |
|---|---|
| **Assistant** | [CATYOUSHA](#catyousha--assistant--chief-of-staff) |
| **Build & Secure** | [JOOBOO](#jooboo--hands-on-cto--full-stack) · [MOTASEM](#motasem--principal-architect) · [YASSER](#yasser--aws--hybridon-prem) · [NAJI](#naji--database-architect--dba) · [RAID](#raid--security) · [YAZEED](#yazeed--ai-lead) · [ASEEL](#aseel--qa--release) · [MOAMEN](#moamen--product--competitive) · [AMANAK](#amanak--program-manager) |
| **Market & Money** | [RAMOUS](#ramous--strategy--partnerships) · [AMER](#amer--sales) · [MAHER](#maher--marketing) · [MURAD](#murad--cfo) · [ABE](#abe--capital--scale) · [ANOOS](#anoos--personal-wealth) · [AHMAD](#ahmad--legal) · [FERAS](#feras--customer-success) |
| **Craft & Comms** | [SAVEE](#savee--creative-director) · [LAMA](#lama--technical-writer) |
| **Wisdom & Self** | [ARWA](#arwa--ethics--islamic-lens) · [MOHAMMAD](#mohammad--psychology) · [TAMER](#tamer--gut-check) |
| **Stress-Test** | [ZOBRONSIKI](#zobronsiki--the-contrarian) · [UNCLE SEINI](#uncle-seini--first-principles) · [JAABARI](#jaabari--the-outsider) |

Full character cards with lane splits, move, and watch notes: [`references/roster.md`](references/roster.md)

---

## How to Use It

**The most common path — call someone by name:**

```
YASSER, cheapest way to run this Postgres?
MURAD, what's the burn impact of hiring two senior engineers?
YAZEED, should we use GPT-4o or Claude for this RAG use case?
```

One member answers directly, in character, in their lane. No roundtable, no ceremony. If it's outside their lane, they hand off instead of bluffing.

**For structured sessions — fire a trigger:**

```
DANGER — should we build this feature in-house or buy it?
THINK — what's the right database for this workload?
CRASH — we're launching in two weeks, what kills us?
```

CATYOUSHA convenes the right voices, runs real disagreement, and closes with a verdict.

Worked examples of both: [`references/examples.md`](references/examples.md)

---

## Triggers

| Trigger | Use it for |
|---|---|
| `RULE` | Remind yourself how the team works |
| `DANGER [topic]` | Options + tradeoffs laid out — you make the call |
| `THINK [topic]` | Team converges to one recommendation |
| `DECIDE [question]` | Fast either/or call, 2–3 voices |
| `PLAN [decision]` | Turn a made decision into owned steps |
| `CRASH [plan]` | Pre-mortem a chosen path |
| `ATTACK [position]` | Devil's-advocate a position you hold |
| `RESEARCH [topic]` | Ground a topic in sourced facts before opinions |
| `RANK` | Daily pulse — what matters today |
| `MEETING` | Credit a past call that proved right |
| `RECOMMENDATION` | Flag a capability gap, propose a new member |

Full specs: [`references/triggers.md`](references/triggers.md)

---

## Keeping Token Costs Down

The skill is designed to stay cheap by default. A few things worth knowing:

**Reference files load on demand, not upfront.** `SKILL.md` is the only file that loads at session start. `roster.md`, `pillars.md`, `triggers.md`, and the rest only come in when the session actually needs them. A single-member call like `MURAD, what's our runway?` never touches the roster file.

**Call one member instead of firing a trigger when you can.** A named call (`JOOBOO, build or buy?`) seats one voice. A trigger (`DANGER — build or buy?`) convenes the full relevant panel. Both are valid — just pick the right tool for the question.

**Keep sessions focused.** The longer the conversation, the more context accumulates. For unrelated questions, start a fresh conversation instead of continuing an old one. Short, purposeful sessions are cheaper and sharper.

**Use `DECIDE` for fast calls.** It's the lightest trigger — 2–3 voices, no ceremony. Reserve `DANGER` and `CRASH` for decisions that actually warrant a full panel.

**On Kiro and tools with `inclusion: manual`:** The steering files won't load unless you explicitly reference them. That's intentional — you control when the team enters context.

---

## Install

### Claude.ai / Claude App

Settings → **Capabilities** → **Skills** → upload a zip of the repo root (`SKILL.md` + `references/`).

The skill loads as a persistent capability in all your Claude conversations. Reference files load on demand; you won't burn context unless you need them.

---

### Claude Code (CLI)

```bash
# Personal (all projects)
cp -r . ~/.claude/skills/the-team/

# Project-only
cp -r . .claude/skills/the-team/
```

---

### Kiro

Kiro uses **steering files**, not `SKILL.md`. The skill ships a ready-made Kiro variant.

**User-level (works across all your projects):**

```
~/.kiro/skills/the-team/
```

Copy `SKILL.md` and the `references/` folder into that path. Kiro will pick it up automatically.

**Workspace-only:**

```
<your-project>/.kiro/steering/
```

Copy the contents of `kiro/.kiro/steering/` into your project's steering folder.

The files use `inclusion: manual` — they don't load by default and won't burn context. Pull the skill in by using a trigger word or member name in chat, or by referencing `#the-team` directly.

> **Note:** Use the Kiro-specific steering variant, not the raw `SKILL.md`. They cover the same ground but are formatted for each tool's loader.

---

### Cursor

```
.cursor/rules/the-team.mdc
```

Or use the cross-client convention:

```
.agents/skills/the-team/
```

Copy `SKILL.md` + `references/` into that folder. Cursor picks up `.cursor/rules/` natively; `.agents/skills/` is the cross-client fallback most tools watch.

---

### VS Code (GitHub Copilot / Copilot Chat)

Copilot reads custom instructions from `.github/copilot-instructions.md`. The simplest approach:

1. Copy the contents of `SKILL.md` into `.github/copilot-instructions.md` in your repo.
2. Create a `references/` folder at the same level and copy the reference files in.
3. In your chat message, reference the file when you want the team: `#file:references/roster.md`

Alternatively, if you're using **VS Code + Cline or Roo Code** (MCP-capable agents), use the `.agents/skills/the-team/` path — those extensions watch it.

---

### Windsurf / Aider / OpenCode / Gemini CLI / Others

```
.agents/skills/the-team/
```

Most agent tools scan `.agents/skills/` as the cross-client convention. Copy `SKILL.md` + `references/` there and it'll be picked up on next load.

---

## Repo Structure

```
the-team-skill/
├── README.md                ← this file
├── SKILL.md                 ← the skill index (always loaded by the agent)
├── references/
│   ├── roster.md            ← character cards — read when convening anyone
│   ├── examples.md          ← worked sessions — read on first run
│   ├── pillars.md           ← per-member Role/Task/Context/Reasoning/Output
│   ├── triggers.md          ← full spec for each trigger
│   └── research.md          ← research protocol + NotebookLM MCP setup
└── kiro/
    └── .kiro/steering/      ← Kiro steering-file variant
```

The lazy-load design is intentional. `SKILL.md` stays thin; reference files load only when the session actually needs them. Sessions stay fast and cheap regardless of how big the roster gets.

---

## Member Quick Reference

### CATYOUSHA — Assistant / Chief of Staff
Runs every session. Opens, routes, tracks actions, closes with a clean synthesis. Always present — never counts as a seated voice.

### JOOBOO — Hands-on CTO / Full-Stack
Leanest way to build it. Team sizing, build-vs-buy, full-stack calls (React, Node/NestJS, APIs). Runs the open-source scan before anything new.

### MOTASEM — Principal Architect
Architecture shape. Minimum cost at the reliability/scale the project actually needs. Decides the pattern; YASSER picks services, NAJI owns data.

### YASSER — AWS & Hybrid/On-Prem
Right AWS service, including new services the week they ship. Also owns on-prem and hybrid — data center stacks, migration paths, Direct Connect, sovereignty requirements.

### NAJI — Database Architect & DBA
Data tier end to end: database selection, modeling, replication/HA, scaling — and day-2 ops (tuning, backup, patching, monitoring).

### RAID — Security
Full surface: supply chain, CVEs, SBOM, compliance by region, threat modeling, hardening, incident response. Has standing flag rights even off-topic.

### YAZEED — AI Lead
Model selection, agents, RAG, evals, guardrails, AI cost. Lives on the frontier; knows what's real vs. hype.

### ASEEL — QA / Release Confidence
Test strategy, regression risk, ship/don't-ship call. The gate between built and deployed.

### MOAMEN — Product & Competitive
What to build next and the market read behind it. Gap analysis, competitor/pricing scans, MVP scoping.

### AMANAK — Program Manager
Sprint planning, cross-product resourcing, dependency mapping, delivery cadence, timeline risk.

### RAMOUS — Strategy & Partnerships
Positioning, moats, market entry, alliances, co-sell, channel/reseller, marketplace.

### AMER — Sales
Pipeline, live deals, objection handling, in-market pricing.

### MAHER — Marketing
Demand gen, channel selection, messaging — minimum spend, maximum reach.

### MURAD — CFO
Runway, burn, margins, unit economics, pricing models.

### ABE — Capital & Scale
Fundraising from pre-seed through growth equity: round sizing, valuation, term sheets, cap table, investor targeting, M&A/exit framing.

### ANOOS — Personal Wealth
Khaled's personal portfolio — ETFs, stocks, position sizing, personal angel bets. Never company capital (that's ABE).

### AHMAD — Legal
Contracts, corporate structure, IP, regulatory, data agreements, equity docs.

### FERAS — Customer Success
Post-sale: onboarding, time-to-value, adoption, churn, renewals, expansion.

### SAVEE — Creative Director
Brand identity, design language, narrative, deck and product UX feel. Translates vibes into structured design specs with real token reasoning.

### LAMA — Technical Writer
Docs, specs, READMEs, customer copy — and the plain-language pass on anything the team produces.

### ARWA — Ethics / Islamic Lens
Shariah-compliance filter, halal/haram, long-term values. Has standing flag rights even off-topic.

### MOHAMMAD — Psychology
Wellbeing, founder pressure, decision psychology, work–life balance.

### TAMER — Gut-Check
The gap between the "smart" answer and what you actually want. Asks the one blunt question everyone else is dancing around.

### ZOBRONSIKI — The Contrarian
Seats by default on `DANGER`, `CRASH`, `ATTACK`. Hunts the failure mode nobody's said out loud yet.

### UNCLE SEINI — First Principles
Seats by default on `DANGER`, `CRASH`, `ATTACK`. Asks whether the team is solving the right problem at all, before debating how.

### JAABARI — The Outsider
Seats by default on `DANGER`, `CRASH`, `ATTACK`. Zero-context read — catches the curse of knowledge before it ships externally.

---

## Caveats

**Quality is model-dependent.** The format works everywhere, but it leans on the host model's ability to hold distinct personas and run real friction. Sharpest on a strong frontier model; flatter on a weak one. Same files, different room.

**NotebookLM integration is third-party.** The setup in [`references/research.md`](references/research.md) uses community-maintained MCP bridges that drive a real Chrome session. Review the repo before granting Google-account access, and never commit the resulting auth tokens — `.gitignore` already blocks the obvious paths.

**This is a personal council, not a marketplace product.** It's tuned to one person's context and judgment. The value is the friction, not the headcount. The members evolve through use — `RANK` and `MEETING` are the growth log.
