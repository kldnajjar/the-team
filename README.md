<div align="center">

# 🧠 the TEAM

**Your own AI advisory council: 17 voices who argue, so you don't decide alone.**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Agent Skill](https://img.shields.io/badge/format-Agent%20Skill-blue)](https://github.com/anthropics/skills)
[![Works with](https://img.shields.io/badge/works%20with-Claude%20%C2%B7%20Claude%20Code%20%C2%B7%20Cursor%20%C2%B7%20Kiro-purple)](#-install)
[![Version](https://img.shields.io/badge/version-2.5.0-orange)](CHANGELOG.md)

[Quick start](#-quick-start) · [Meet the team](#-meet-the-team) · [Triggers](#-triggers) · [How it works](#-how-it-works) · [Install](#-install) · [FAQ](#-faq)

</div>

---

## Why

Ask one AI a question and you get one confident answer. Often it's the answer you were hoping for.

**the TEAM** turns that single answer into a meeting. An architect, a CFO, a lawyer, a security lead and others each give their view **from their own lane**. Three stress-testers attack the plan, one upside voice asks if you're aiming too small, and a chief of staff closes with **one recommendation and one next step**.

- 🎯 **Only the right people speak:** 2–3 leads per topic, not 17 voices nodding along.
- ⚔️ **Real disagreement:** on Claude Code each voice thinks independently, then answers are peer-reviewed **anonymously**, following Karpathy's [LLM Council](https://github.com/karpathy/llm-council) pattern.
- 🧰 **Uses real tools:** advisors call installed skills (e.g. the Claude **sales** skills for pipeline, deals and forecasts) instead of guessing.
- 🐟 **Simulates the market:** `SIMULATE` runs a [MiroFish](https://github.com/666ghj/MiroFish) crowd simulation when the question is "how will people react?"
- 📊 **Polished HTML report:** every big session can produce a shareable report with the verdict, every voice, the blind review and the evidence.
- 📓 **Learns from outcomes:** a decision journal records who called it right.
- 💸 **Cheap by default:** only `SKILL.md` loads at start; everything else loads on demand.

---

## ⚡ Quick start

**1. Install** (Claude Code):
```bash
git clone https://github.com/kldnajjar/the-team ~/.claude/skills/the-team
```

**2. Ask one advisor by name** (the most common use):
```text
MOTASEM, cheapest way to run a 200 GB Postgres in eu-central-1?
AMER, prep me for tomorrow's call with the bank.
ABE, what does losing this deal do to our quarter?
```

**3. Or convene the room for a big decision:**
```text
DANGER: launch SaaS first or self-hosted first?
```

What you get back (shortened):
```text
CATYOUSHA: close
  Agree:          one shared image for both deployment models
  Clash:          RAMOUS says self-hosted is the entry ticket; JOOBOO says SaaS protects the team
  Blind spot:     nobody named the first paying customer (UNCLE SEINI)
  Recommendation: SaaS first, Helm one release behind; flip if a regulated buyer commits
  Next move:      list the 3 likeliest first customers and their deployment constraint
```

Full worked sessions: [`references/examples.md`](references/examples.md)

---

## 👥 Meet the team

Each member has one job. If you ask them something outside it, they hand you to the right person instead of bluffing.

### 🗂️ The chair

| | Member | What they do | Ask them when… | Try |
|---|---|---|---|---|
| 🗂️ | **CATYOUSHA** | Chief of staff. Runs every session, keeps score, writes the close. | You want the room organised or a daily pulse. | `RANK` |

### 🛠️ Build

| | Member | What they do | Ask them when… | Try |
|---|---|---|---|---|
| 🧑‍💻 | **JOOBOO** | CTO. How to build it, with how many people, and is it safe to ship. | Build vs buy, team size, release calls. | `JOOBOO, rewrite or refactor?` |
| 📅 | **AMANAK** | Program manager. Turns a decision into a spec, tickets and a plan, and runs coding agents to deliver it. | Planning, sprints, "are we on track?", breaking work down for agents. | `PLAN: the SaaS-first launch` |
| 🏗️ | **MOTASEM** | Architect. Cloud, on-prem/hybrid and databases at the lowest cost that still meets the SLA. | Which AWS service, which database, which region, DR. | `MOTASEM, DynamoDB or Aurora?` |
| 🛡️ | **RAID** | Security, vulnerabilities & regulation. Finds the hole and names the rule it breaks. | CVEs, dependencies, NCA / SAMA / PDPL / GDPR / EU AI Act. | `RAID, is this bucket policy safe?` |
| 🤖 | **YAZEED** | AI engineer. Picks the model, builds the agent, knows the cost per call. | Models, RAG, agents, evals, AI cost. | `YAZEED, Sonnet or Haiku here?` |

### 💼 Market & Money (powered by the Claude **sales** skills)

| | Member | What they do | Ask them when… | Try |
|---|---|---|---|---|
| ♟️ | **RAMOUS** | Product & strategy. What to build, where to play, which partner opens the door. | Roadmap, competitors, positioning, partnerships. | `RAMOUS, research this prospect` |
| 🤝 | **AMER** | Go-to-market. Sells it, markets it, keeps the customer. | Call prep, objections, deals, pipeline, churn. | `AMER, they said we're too expensive` |
| 💰 | **ABE** | CFO. Runway, margins, pricing, forecasts and fundraising. | Cost of a decision, forecast, raising money. | `ABE, what if this deal slips?` |
| ⚖️ | **AHMAD** | Lawyer. Finds the clause that bites later. | Contracts, entity structure, IP, data terms. | `AHMAD, review this MSA clause` |

### ✍️ Craft · 🧭 Values & self

| | Member | What they do | Ask them when… | Try |
|---|---|---|---|---|
| 🎨 | **SAVEE** | Writing & design. Makes it clear and makes it look intentional. | Docs, decks, copy, brand, UI specs. | `SAVEE, make this README human` |
| 🌙 | **ARWA** | Ethics & Islamic lens. Is it right, and is it halal? | Revenue models, investments, values calls. | `ARWA, is this pricing model OK?` |
| 🫂 | **MOHAMMAD** | Gut-check & wellbeing. Asks what you actually want, and notices the pressure. | The "smart" answer doesn't feel right. | `MOHAMMAD, am I burning out on this?` |

### 🔥 The stress-testers

They have **no expert lane on purpose**. Three of them attack the plan, and one pushes it to be bigger, so the close is neither reckless nor timid. ZOBRONSIKI, UNCLE SEINI and JAABARI join every `DANGER`, `CRASH` and `ATTACK`; IDREES joins every `DANGER` and `DEEP` run.

| | Member | Their one question | What it catches |
|---|---|---|---|
| 😈 | **ZOBRONSIKI** | "How does this fail?" | The risk everyone agreed not to mention |
| 🔍 | **UNCLE SEINI** | "Are we solving the right problem?" | A great answer to the wrong question |
| 👀 | **JAABARI** | "Would a stranger understand this?" | Jargon and insider assumptions, before a customer sees them |
| 🚀 | **IDREES** | "What if we're thinking too small?" | The bigger win: an "and" where you assumed "or" |

Full character cards: [`references/roster.md`](references/roster.md) · Per-member prompts: [`references/pillars.md`](references/pillars.md) · Skills each member uses: [`references/skills-map.md`](references/skills-map.md)

---

## 🎛️ Triggers

| Trigger | What it does | Example |
|---|---|---|
| `DANGER` | Lays out options and tradeoffs; you decide | `DANGER: raise now or in two quarters?` |
| `THINK` | The team agrees on one answer | `THINK: which region for the EU launch?` |
| `DECIDE` | Fast either/or in a few lines | `DECIDE: Slack or Teams for the client?` |
| `PLAN` | Turns a decision into owned steps | `PLAN: the SaaS-first launch` |
| `CRASH` | Pre-mortem: "it's a year later and this failed. Why?" | `CRASH: launch in 3 weeks` |
| `ATTACK` | The strongest case against your position | `ATTACK: I think we should drop Azure` |
| `RESEARCH` | Current, sourced facts before opinions | `RESEARCH: competitor pricing in KSA` |
| `SIMULATE` | Crowd simulation of how people would react (MiroFish) | `SIMULATE: banks react to usage-based pricing` |
| `RANK` | Daily pulse: top 3 things for today | `RANK` |
| `MEETING` | Credit a past call that proved right | `MEETING` |
| `META` | Tune the team using journal outcomes | `META` |
| `RECOMMENDATION` | Is a lane missing from the team? | `RECOMMENDATION` |
| `RULE` | Print the cheat sheet | `RULE` |

Add `DEEP` to any big trigger (`DANGER DEEP: …`) for the full run: forced debate, options ranking and an optional simulation. Full specs: [`references/triggers.md`](references/triggers.md)

---

## ⚙️ How it works

```text
 Your question
     │
     ▼
 0. FRAME       CATYOUSHA: checks past decisions, flags biased wording, writes a 300-word brief
     │
     ▼
 1. INDEPENDENT 2–3 leads + stress-testers answer alone, in parallel, each with a confidence block
     │          (JAABARI only sees what a customer would see)
     ▼
 2. BLIND REVIEW answers shuffled to A/B/C; leads rank them without knowing who wrote what
     │
     ▼
 3. DEBATE      if everyone agrees too easily → ZOBRONSIKI attacks, top lead defends
     │
     ▼
 4. CLOSE       agree → clash → blind spot → ONE recommendation → ONE next move (+ dissent ledger)
     │
     ▼
 5. REPORT      polished HTML report + decision appended to .the-team/journal.jsonl
```

| Mode | Used by | Cost |
|---|---|---|
| Quick | `DECIDE`, `THINK`, name-calls | 1–4 model calls |
| Standard | `DANGER`, `CRASH`, `ATTACK` | ~10–14 calls |
| Deep | `… DEEP` | 16+ calls |

On hosts without subagents (e.g. claude.ai chat), one model plays each voice in turn and the same steps still apply. Details: [`references/parallel-mode.md`](references/parallel-mode.md)

### 📊 The report

Standard and Deep runs fill [`assets/report-template.html`](assets/report-template.html): one self-contained file with no external assets, light and dark mode, and print-ready. It shows confidence and consensus, the verdict and next move, agree / clash / blind spots, the upside check, every voice with its confidence, the blind peer-review table, the debate, ranked options, evidence tagged *verified / inferred / simulated*, the dissent ledger, and a copyable journal entry. Open the template in a browser to see a sample.

### 🧰 Companion skills

When a skill is installed, the owning member uses it, then speaks the result in their own voice:

- **AMER** → `sales:call-prep`, `sales:handle-objection`, `sales:deal-review`, `sales:close-plan`, `sales:pipeline-review`
- **RAMOUS** → `sales:account-research`, `sales:competitive-intelligence`, `sales:account-plan`
- **ABE** → `sales:forecast`, `sales:deal-slip-scenario`, `sales:win-loss-review`
- **AMANAK** → [AI Hero](https://www.aihero.dev/skills-catalog) skills (`/grill-with-docs`, `/to-spec`, `/to-tickets`, `/implement-spec`, `/handoff`, `/retro`), plus Google [Harness²](https://github.com/google-research/harness2) to tune the TEAM itself in `META`
- **SAVEE** → a full UI/UX stack: [`ui-ux-pro-max`](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) (design system), `frontend-design` (build), Vercel's [`web-design-guidelines`](https://github.com/vercel-labs/agent-skills) and `design:accessibility-review` (review), `design:ux-copy`, `design:design-handoff`
- **MOTASEM / JOOBOO / YAZEED** → engineering, AWS and Bedrock skills

No skill installed? The member answers unaided and says so. Edit the full map in [`references/skills-map.md`](references/skills-map.md).

### 🐟 Market simulation (MiroFish)

`SIMULATE` seeds [MiroFish](https://github.com/666ghj/MiroFish), an open-source multi-agent prediction engine, with your pricing page, launch post or policy text, then simulates how a crowd of agents reacts. ZOBRONSIKI and JAABARI attack the result, and every finding is tagged **simulated**, never *verified*. No MiroFish? A built-in lite panel of 6 to 8 audience archetypes stands in. Setup and rules: [`references/simulation.md`](references/simulation.md)

---

## 📦 Install

| Tool | How |
|---|---|
| **Claude Code** | `git clone https://github.com/kldnajjar/the-team ~/.claude/skills/the-team` (or `.claude/skills/the-team` for one project) |
| **Claude app** (claude.ai / Desktop) | `git archive --format=zip --prefix=the-team/ -o the-team.zip HEAD`, then upload the zip in your Skills settings |
| **Cursor, Windsurf, Cline, Gemini CLI, OpenCode** | Copy `SKILL.md` + `references/` to `.agents/skills/the-team/` (or the tool's rules folder) |
| **Kiro** | `git clone https://github.com/kldnajjar/the-team ~/.kiro/skills/the-team` (or `.kiro/skills/the-team` for one project). Kiro reads `SKILL.md` and loads `references/` on demand |

**Optional extras:** the Claude **sales** plugin (for Market & Money), AI Hero skills via `npx skills add mattpocock/skills -y -g` (for AMANAK), `ui-ux-pro-max` and `web-design-guidelines` (for SAVEE), a MiroFish instance (for `SIMULATE`), and a NotebookLM MCP (for `RESEARCH`, see [`references/research.md`](references/research.md)).

---

## 📁 Repo structure

```text
the-team/
├── SKILL.md                  # entry point, always loaded
├── references/
│   ├── roster.md             # who everyone is
│   ├── pillars.md            # each member's prompt: Role/Task/Context/Reasoning/Stop/Output
│   ├── triggers.md           # every trigger, specified
│   ├── parallel-mode.md      # modes, blind review, debate, decision journal
│   ├── skills-map.md         # which installed skills each member uses
│   ├── simulation.md         # SIMULATE with MiroFish
│   ├── research.md           # research protocol + NotebookLM
│   └── examples.md           # worked sessions
├── assets/report-template.html # the HTML council report
├── evals/test-prompts.md     # run after every edit
├── CHANGELOG.md
└── LICENSE
```

---

## ❓ FAQ

**Is it 17 separate AIs?** No. It's one skill. On Claude Code each voice runs as its own subagent, which makes the independence real; elsewhere one model voices them in turn.

**Won't it be slow and expensive?** A name-call is a single answer. Only `DANGER` / `CRASH` / `ATTACK` convene the room, and `DEEP` is opt-in.

**Can I make it mine?** Yes. Fork it and rewrite `references/roster.md`. Names, lanes and skills are all plain markdown. Run `evals/test-prompts.md` after editing.

**Is the MiroFish simulation "real data"?** No. It's a model of a crowd. Use it to find what to test with real customers, not as proof.

**Will it hijack normal messages?** No. A trigger is the word in capitals at the start of a message, and a name only counts when you address the member. "Email Ahmad the SOW" is about a real person, so nobody speaks.

**Is it professional advice?** No. The lawyer, CFO, ethics and wellbeing voices name the issue and tell you when a qualified person has to sign off.

**Why the personal names?** It began as one person's council, modelled on people whose judgement he trusts. The structure is generic; the names are yours to change.

---

## 🤝 Contributing

Issues and PRs welcome, especially new worked examples, skill mappings, and eval prompts. Keep `SKILL.md` lean: new detail goes in `references/`. Every PR that changes behaviour should add or update a line in `evals/test-prompts.md` and `CHANGELOG.md`.

## 🙏 Credits

Council method inspired by [karpathy/llm-council](https://github.com/karpathy/llm-council) and the community council skills ([aiwithremy](https://github.com/aiwithremy/claude-skills-llm-council), [evisoft](https://github.com/evisoft/council), [torpedod](https://github.com/torpedod/claude-council)). UI/UX skills by [nextlevelbuilder](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) and [Vercel](https://github.com/vercel-labs/agent-skills). Delivery workflow skills by [AI Hero / Matt Pocock](https://github.com/mattpocock/skills). Harness self-improvement by Google Research [Harness²](https://github.com/google-research/harness2) (Apache-2.0). Crowd simulation by [MiroFish](https://github.com/666ghj/MiroFish) (AGPL-3.0, used as an external service, not bundled).

## 📄 License

[MIT](LICENSE) © 2026 Khaled Al Najjar
