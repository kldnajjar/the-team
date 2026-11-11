# Changelog

## 2.5.0 — 2026-11-11

Audit pass.

### Fixed
- **False triggers:** a trigger now needs CAPITALS at the start of the message, and a name only counts when the member is addressed. Mentions of real people who share a member's name no longer call a persona.
- **Seating gaps:** `SIMULATE`, `RESEARCH` and `META` added to the stress-tester rule; `RANK` no longer contradicts it.
- **`THINK`** was described as both "a few lines" and a five-part close; it is now Quick engine with a one-line-per-part close.
- **Single-pass fallback** no longer skips the answer round or pretends to run a blind review.
- **Peer review:** leads no longer score their own answer.
- **Report:** `<` in JSON strings is escaped so quoted text can't break the page; chat hosts offer the report instead of building it every run; sample data now includes all seated voices.
- Worked `DANGER` example now shows the confidence header and dissent line the protocol requires.
- Stale roster count, a leftover JOOBOO stop condition, two typos.

### Added
- **Honest limits** (legal, finance, Shariah, wellbeing) and **ask before acting** rules.
- `META` defaults to diff + regression prompts (`skill-creator`); Harness² marked experimental.
- More companion skills mapped: `metrics-review`, `brand-review`, `engineering:documentation`, `engineering:debug`, `stakeholder-update`, `prompt-master`, `seo-audit`, AWS MCP tools.
- Seven regression prompts (25–31).
- **`SIMULATE` lite panel:** a built-in stand-in for when MiroFish isn't reachable, tagged *simulated (lite)*.

### Changed
- Worked examples and the sample report now use a made-up product ("Lumen") instead of real product internals. Member names are unchanged.
- Per-member stack and region settings are now defaults, used only when the topic names none.
- Kiro install uses Kiro's native skills folder (`~/.kiro/skills/`) instead of flattened steering files.

## 2.4.0 — 2026-11-09

### Added
- **SAVEE UI/UX stack** (`skills-map.md` → Craft): `ui-ux-pro-max` (design system), Claude Design / Design System artifact types, `frontend-design`, Vercel `web-design-guidelines`, `design:design-critique`, `design:accessibility-review` (WCAG 2.1 AA), `design:ux-copy`, `design:design-handoff`, `dataviz`.
- SAVEE's default pre-ship review loop (critique → guidelines → accessibility → copy, top 3 issues) and an Arabic/RTL check.

## 2.3.0 — 2026-11-09

### Added
- **AMANAK is back** as Program Manager: delivery and agentic execution. He owns `PLAN` (decision → spec → agent-sized tickets → ordered owners), sprint planning, the critical path and resourcing collisions, and co-owns `META`.
- **AI Hero skills** ([mattpocock/skills](https://github.com/mattpocock/skills)) mapped to AMANAK (`/grill-with-docs`, `/wayfinder`, `/to-spec`, `/to-tickets`, `/triage`, `/implement-spec`, `/handoff`, `/retro`) and JOOBOO (`/implement`, `/tdd`, `/diagnosing-bugs`, `/improve-codebase-architecture`).
- **Google Harness²** for `META`: AMANAK can run it against the TEAM's own harness and bring back proposed edits for review. Never auto-applied; network and data limits flagged.

### Changed
- JOOBOO narrowed to build & release; scheduling and sequencing moved to AMANAK.

## 2.2.0 — 2026-11-09

### Added
- **IDREES, the Expansionist:** a fourth stress-tester and the council's upside voice ("what if we're thinking too small?"). Seats by default on `DANGER` and `DEEP`. The close now states whether his bigger play was adopted, deferred or rejected.
- **Polished HTML report** (`assets/report-template.html`): self-contained, light and dark mode, print-ready. Renders from a single JSON block; schema in `parallel-mode.md`.

## 2.1.0 — 2026-11-09

### Added
- **Companion skills** (`references/skills-map.md`): RAMOUS, AMER and ABE use the Claude **sales** skills (account research, competitive intel, call prep, objections, deal review, close plan, pipeline, forecast, slip scenarios). Other members are mapped to engineering, AWS, Bedrock and design skills.
- **`SIMULATE` trigger** (`references/simulation.md`): MiroFish crowd simulation for "how will people react?" decisions; results tagged *simulated*.
- **Modes:** Quick / Standard / Deep (`DEEP` suffix).
- **Sharper protocol** (`parallel-mode.md`): journal lookup + bias audit at framing; confidence block per voice; outsider asymmetry for JAABARI; consensus score with a conditional Prosecutor/Defender debate; dissent ledger; chair may side with a lone dissenter; Markdown report in Claude Code.
- **Optional multi-model council** via LiteLLM / OpenRouter.
- **`META` trigger:** tune personas from journal outcomes.

### Changed
- README rebuilt as an open-source landing page: a "Meet the team" card for each member, flow diagram, install matrix, FAQ, contributing, credits.

## 2.0.0 — 2026-11-09

### Changed
- **Roster cut from 26 to 15 voices.** Overlapping lanes merged:
  - MOTASEM now covers cloud, hybrid/on-prem and the data tier (absorbs YASSER and NAJI).
  - JOOBOO now covers build, delivery and release (absorbs AMANAK and ASEEL).
  - RAMOUS now covers product and strategy (absorbs MOAMEN).
  - AMER now covers the full go-to-market motion (absorbs MAHER and FERAS).
  - ABE now covers finance and capital (absorbs MURAD).
  - SAVEE now covers writing and design (absorbs LAMA).
  - MOHAMMAD now covers gut-check and wellbeing (absorbs TAMER).
- RAID refocused on security, vulnerabilities and regulation; YAZEED retitled AI engineer.
- Stress-test voices (ZOBRONSIKI, UNCLE SEINI, JAABARI) rewritten in plain language with an example each.
- Worked examples refreshed for current work; outdated product context and invented "ex-FAANG" bios removed.
- `SKILL.md` description shortened from 961 to ~620 characters (limit: 1024).
- README de-duplicated; install steps now match what the repo actually ships.

### Added
- `references/parallel-mode.md`: independent subagent round + anonymous peer review for `DANGER`, `CRASH`, `ATTACK`.
- Decision journal (`journal.jsonl`) backing `MEETING` and `RANK`.
- `evals/test-prompts.md`: regression prompts.
- MIT `LICENSE`.

### Removed
- ANOOS (personal investing); use the `safe-us-stock-trading` skill.
- `.gitignore` rules and README sections for a Kiro variant folder that never existed.

## 1.0.0
- Initial 25-member council.
