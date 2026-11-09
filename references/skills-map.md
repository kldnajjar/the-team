# Companion skills

Members don't work bare-handed. When a companion skill is installed in the current host, the member **invokes it** to do the heavy lifting (pull CRM data, read transcripts, build a plan), then delivers the result **in their own voice, in their own lane**. If the skill isn't installed, the member answers unaided and says so in one line; never pretend a skill ran.

Rules:
- Invoke only the one skill the question actually needs, not a chain "just in case".
- Skill output is evidence, not the verdict. It still goes through the merit audit and the stress-test voices.
- On name-calls, the member may invoke the skill directly. In a trigger, the lead whose lane owns it invokes it once and shares the result with the room.

---

## Market & Money → the Claude **sales** plugin (primary)

### RAMOUS: Product & Strategy
| Question | Skill |
|---|---|
| "Research [company]" / is it a fit for our ICP? | `sales:account-research` |
| Competitor play, battlecard, win/loss vs a rival | `sales:competitive-intelligence` |
| Strategic plan for a key account | `sales:account-plan` |
| Where can we expand / upsell? | `sales:expansion-whitespace` |
| Which accounts deserve our focus? | `sales:account-tiering` |
| What are customers actually saying about X? | `sales:customer-voice` |
| Also useful | `product-management:competitive-brief`, `product-management:roadmap-update`, `product-management:write-spec` |

### AMER: Go-to-Market
| Question | Skill |
|---|---|
| Prep me for this call | `sales:call-prep` |
| Process this call / transcript | `sales:call-summary` |
| Draft outreach or a sequence | `sales:draft-outreach` |
| "They said we're too expensive" | `sales:handle-objection` |
| Is this deal going to close? | `sales:deal-review` |
| What's missing to move this deal? | `sales:deal-advance-gap` |
| Path to signature / mutual action plan | `sales:close-plan` |
| Who are the players? Am I single-threaded? | `sales:stakeholder-map` |
| Pipeline health | `sales:pipeline-review` |
| Score an inbound lead | `sales:lead-triage` |
| Customer health / QBR / renewals | `sales:customer-health`, `sales:renewal-radar` |
| Deck, one-pager, leave-behind | `sales:create-an-asset` |
| Also useful | `marketing:campaign-plan`, `marketing:email-sequence`, `marketing:content-creation` |

### ABE: CFO, Finance & Capital
| Question | Skill |
|---|---|
| Commit / best case / pipeline narrative | `sales:forecast` |
| What if this deal slips? | `sales:deal-slip-scenario` |
| Coverage vs target | `sales:pipeline-review` |
| Why do we win or lose? (revenue quality) | `sales:win-loss-review` |
| Build a financial model / sheet | Sheets artifact, or the `xlsx` skill when a file is required |

### AHMAD: Legal
No sales skill owns legal. AHMAD reviews the terms produced by `sales:close-plan` and `sales:create-an-asset` (pricing promises, SLAs, data clauses) before they go out. For contract files, use the `docx` skill.

---

## Build & Delivery

### AMANAK: Program Manager → AI Hero skills + Google Harness²

**AI Hero** ([mattpocock/skills](https://github.com/mattpocock/skills), free, open source; Claude Code and any agent reading `~/.claude/skills`):
```bash
npx skills add mattpocock/skills -y -g     # drop -g to install per project
```

| Question | Skill |
|---|---|
| "Is this plan actually decided?" Grill it and record the decisions | `/grill-with-docs` (or `/grill-me` for a quick pass) |
| A big, foggy effort | `/wayfinder`: chart it as decisions to settle, then settle them |
| Turn the agreed plan into a spec | `/to-spec` |
| Split the spec into agent-buildable tickets | `/to-tickets` |
| Sort a pile of raw issues | `/triage` |
| Build a whole spec with parallel coding agents | `/implement-spec` (JOOBOO owns the code review gate) |
| Pass a long session to another agent | `/handoff` |
| What should change after this sprint? | `/retro` |
| Questions someone else must answer | `/to-questionnaire` |
| Also useful | `product-management:sprint-planning`, `productivity:task-management`; Jira through the Atlassian connector for real tickets |

**Google Harness²** ([google-research/harness2](https://github.com/google-research/harness2), Apache-2.0): a research framework that improves an agent's **harness** (system prompt, guardrails, memory, skills, tool guidance, scripts, subagents, plugins) while the model stays fixed. It proposes edits, tests them, and keeps an improvement library (`EXPERIENCE.md`).

AMANAK uses it in `META` to tune **the TEAM itself**: run a batch of past journal questions through the skill, let Harness² propose edits to `roster.md`, `pillars.md` or `triggers.md`, then bring the proposed diff to Khaled. He never auto-applies changes.

```bash
git clone https://github.com/google-research/harness2 && cd harness2
uv venv --python 3.12 .venv && source .venv/bin/activate
uv pip install -e '.[render]'
harness2-demo --output runs/demo --k 2      # no-credentials demo
# model-backed runs: Node 20+, gcloud ADC, a Vertex AI project + model IDs in .env
```

**Limits (RAID's flags):**
- Linux, Python 3.12 only.
- Executors are OpenCode (default) and Codex (`--substrate cx`); Claude Code isn't a listed executor yet.
- Execution substrates have **unrestricted network by default** and Codex runs with its sandbox off. Restrict egress, and never point it at client data.
- It's a research project, "not an officially supported Google product", and its benchmark gains are author-reported. Start with a handful of tasks; you pay all inference.

## Other members

| Member | Companion skills |
|---|---|
| **CATYOUSHA** | `sales:daily-briefing` / `sales:weekly-wrap` (feeds `RANK`), `productivity:task-management` (feeds `PLAN`) |
| **JOOBOO** | `engineering:code-review`, `engineering:testing-strategy`, `engineering:deploy-checklist`, `engineering:tech-debt`; AI Hero `/implement`, `/tdd`, `/diagnosing-bugs`, `/improve-codebase-architecture`, `/prototype` |
| **MOTASEM** | `engineering:architecture`, `engineering:system-design`, `aws-sow-generator`, `aws-rapid-assessment` |
| **RAID** | `engineering:incident-response`, `engineering:code-review` (security focus) |
| **YAZEED** | `bedrock-model-selector`, `aiaf-assessment-report`, `aws-data-ai-readiness-assessment` |
| **SAVEE** | `humanizer`, `design:design-critique`, `design:ux-copy`, `frontend-design` |
| **RESEARCH** trigger | `deep-research`, `fact-checker` |
| **SIMULATE** trigger | MiroFish (external engine, see `simulation.md`) |

Skill names follow the Claude plugin naming (`plugin:skill`). If your install uses different names, edit this table; nothing else in the TEAM depends on them.
