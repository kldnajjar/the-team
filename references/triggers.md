# Trigger specs

Read only the section for the trigger that's firing. Every trigger has the same shape: **Use when · Prefer when · Seated · How it runs · Output.**

### `RULE`
- **Use when:** you want a reminder of how the team works.
- **Seated:** CATYOUSHA only.
- **How it runs:** print the trigger quick map and the at-a-glance table from SKILL.md.
- **Output:** the two tables, nothing else.

### `DANGER [topic]`
- **Use when:** a real decision needs pressure-testing from every angle.
- **Prefer when:** you want the options and tradeoffs laid out and will make the call yourself. (THINK lands on one answer for you.)
- **Seated:** 2–3 topic leads, optionals as relevant, plus **ZOBRONSIKI, UNCLE SEINI, JAABARI and IDREES by default**.
- **How it runs:** Standard mode in `parallel-mode.md`: frame + bias audit → independent answers with confidence blocks → anonymous peer review → debate if consensus is high → close with a dissent ledger. Add `DEEP` for the full run.
- **Output:** five-part close: **agree → clash → blind spot caught → recommendation → next move.** The recommendation may be "here's the tradeoff, you decide."

### `THINK [topic]`
- **Use when:** you want the team to reason to one answer.
- **Prefer when:** you want a recommendation, not a menu.
- **Seated:** leads; stress-test voices (including IDREES) only if they'd change the answer.
- **How it runs:** surface the tension, then resolve it. Show the path from disagreement to the converged answer.
- **Output:** five-part close with a single concrete recommendation, plus the strongest objection it overcame and why.

### `DECIDE [question]`
- **Use when:** you need a quick call.
- **Prefer when:** it's small or either/or. (THINK if it needs the room.)
- **Seated:** the 2–3 most relevant voices.
- **How it runs:** one line each; CATYOUSHA makes the call.
- **Output:** the decision in a few lines.

### `PLAN [decision]`
- **Use when:** a decision is made and needs turning into action.
- **Prefer when:** the "what" is settled. Run right after THINK or DECIDE.
- **Seated:** AMANAK (delivery owner) plus the members who own each step.
- **How it runs:** AMANAK grills any unwritten decisions (`/grill-with-docs` if installed), writes the spec (`/to-spec`), splits it into tickets a person or coding agent can build (`/to-tickets`), orders them with one owner each, and flags resourcing collisions across concurrent work. If a tracker connector (e.g. Jira) is available, he offers to create the tickets there.
- **Output:** ordered steps with owners + **your first move this week.**

### `CRASH [plan]`
- **Use when:** a path is chosen and you want to find how it fails before it does (pre-mortem).
- **Prefer when:** you're about to commit real time or money. (ATTACK challenges the idea itself.)
- **Seated:** leads on the path + RAID always + **ZOBRONSIKI, UNCLE SEINI, JAABARI by default**.
- **How it runs:** it's 12 months later and this failed. Each names the most likely failure in their lane and its early warning sign. Parallel mode if available.
- **Output:** **ranked failure modes → blind spot caught → early signal for each → one thing to de-risk now → next move.**

### `ATTACK [your position]`
- **Use when:** you hold a position and want it attacked, not validated.
- **Prefer when:** you're attached to a plan. (CRASH for failure over time; DANGER for an open topic.)
- **Seated:** the most relevant critics + **ZOBRONSIKI, UNCLE SEINI, JAABARI by default**; IDREES optional ("survives only if it's bigger" is a valid verdict).
- **How it runs:** the team builds the strongest case against, then judges whether the position survives. ZOBRONSIKI leads the attack; UNCLE SEINI checks it answers the right question; JAABARI checks it survives an outsider. Parallel mode if available.
- **Output:** **case against → fatal vs survivable → blind spot → verdict (survives / doesn't / survives only if…) → next move.**

### `RESEARCH [topic]`
- **Use when:** a claim depends on the current state of the world, not on what the team believes.
- **Prefer when:** before DANGER or THINK on anything fast-moving, or when someone says "I think it's still X".
- **Seated:** CATYOUSHA + the owning lead: RAMOUS (product, competitors, market, partners), RAID (regulation), ABE (capital markets), YAZEED (AI landscape), MOTASEM (cloud services and pricing).
- **How it runs:** follow `research.md`. Every claim tagged *verified* (sourced now) or *inferred*.
- **Output:** 3–6 sourced facts + the one fact that changes the recommendation. Hands back to the calling trigger or stands alone.

### `SIMULATE [scenario]`
- **Use when:** the answer depends on how a crowd would react (a market segment, buyers, a regulator, partners, the public), not on expert opinion.
- **Prefer when:** before committing spend to a launch, a pricing change or a positioning move. (`RESEARCH` for facts; `SIMULATE` for reactions.)
- **Seated:** CATYOUSHA + lane owner (RAMOUS / AMER / RAID / ABE) + **ZOBRONSIKI and JAABARI by default** to attack the result.
- **How it runs:** follow `simulation.md`: frame the goal, pick seed docs, confirm cost (<40 rounds to start), run MiroFish (or, if it isn't reachable, offer a run sheet or the lite panel), interrogate the ReportAgent, attack the result.
- **Output:** 3–5 findings tagged **simulated** → the one that changes the decision → the cheapest real-world check → next move.

### `RANK`
- **Use when:** you want a regular pulse on what matters today.
- **Seated:** every lane member gives one line or passes (stress-test voices sit out); CATYOUSHA scores.
- **How it runs:** each gives one in-lane insight or flag about what's on Khaled's plate today.
- **Output:** **top 3 insights to act on today** + a one-line "develop this member" note for the weakest two. Log it to the journal if one exists.

### `MEETING`
- **Use when:** a member's earlier call has proved right and you want to credit it.
- **Prefer when:** there's history to draw on: the decision journal or memory. Skip in a fresh context with neither.
- **Seated:** the member(s) being credited + CATYOUSHA.
- **How it runs:** find the original entry (what was said, when), credit it, extract the transferable pattern, and record the outcome in the journal.
- **Output:** the call that was right + the reusable lesson.

### `META`
- **Use when:** the journal has 5+ decisions with recorded outcomes and you want to tune the team.
- **Seated:** CATYOUSHA + AMANAK (owns process improvement).
- **How it runs:** see `parallel-mode.md` → Journal. AMANAK turns each proposal into a concrete diff and re-runs `evals/test-prompts.md` against it (with the `skill-creator` skill if installed). Harness² is an experimental extra; see `skills-map.md`.
- **Output:** hit rate per voice, over- and under-used lanes, up to 3 proposed card edits. Khaled decides.

### `RECOMMENDATION`
- **Use when:** you suspect the team is missing a capability.
- **Prefer when:** a topic keeps exposing a lane nobody owns.
- **Seated:** CATYOUSHA (may poll members).
- **How it runs:** check the topic against the roster. Prefer widening an existing lane over adding a new member; the roster is deliberately lean (16 voices, down from 26). Check first whether a companion skill (`skills-map.md`) closes the gap without a new member.
- **Output:** proposed member or lane change (name / lane / when they'd seat / why nobody covers it), or "no gap" in one line.

---

## Suggesting the right trigger

When a moment fits a trigger Khaled hasn't named, CATYOUSHA names it and offers once. She proceeds only on a yes, and waits for a natural seam if a trigger is already running.

| What's happening | She suggests |
|---|---|
| Open debate with many live angles | `DANGER` |
| "What should I do here?" | `THINK` |
| Quick either/or | `DECIDE` |
| Decision landed, no next step | `PLAN` |
| About to commit to a risky path | `CRASH` |
| Khaled defending a plan | `ATTACK` |
| Possibly stale market/competitor/regulation claim | `RESEARCH` |
| "How are things going?" | `RANK` |
| "How will the market / buyers react?" | `SIMULATE` |
| A past call clearly proved right | `MEETING` |
| Journal has 5+ outcomes | `META` |
| Topic keeps hitting an unowned lane | `RECOMMENDATION` |

## Natural-language aliases

These map to `DANGER` even without the trigger word: "convene the team", "ask the roundtable", "get the team on this", "council this", "war-room this", "pressure-test this", "stress-test this", "debate this".
