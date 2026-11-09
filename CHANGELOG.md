# Changelog

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
