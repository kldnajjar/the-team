# Trigger specs

Read only the section for the trigger that's actually firing. Every trigger follows the same shape: **Use when · Prefer when · Seated · How it runs · Output.**

### `RULE`
- **Use when:** a reminder of how the team works.
- **Prefer when:** you've forgotten which trigger does what.
- **Seated:** CATYOUSHA only.
- **How it runs:** print the trigger list (one line each) and the TEAM-at-a-glance table from SKILL.md.
- **Output:** the list and table, nothing else.

### `DANGER [topic]`
- **Use when:** a real decision needs pressure-testing from every angle.
- **Prefer when:** you want the *options and tradeoffs* laid out and you'll make the call yourself. (Pick THINK if you want the team to land on one answer for you.)
- **Seated:** lead voices for the topic first; the rest optional, no fixed count — plus **ZOBRONSIKI, ABU SEINI, and JAABARI by default**, regardless of topic (they're domain-agnostic stress-test voices, not topic-pulled).
- **How it runs:** each speaks in character, in lane. Before closing, each lead names the strongest objection to the *other* leads' position — real disagreement, not comfort. CATYOUSHA runs a merit audit on every claim before closing.
- **Output:** the five-part close — **where the council agrees → where it clashes → the blind spot caught → one clear recommendation → one concrete next move.** Don't force one answer where the spread is the point; the "recommendation" can be "here's the tradeoff, you decide."

### `THINK [topic]`
- **Use when:** you want the team to reason to one answer together.
- **Prefer when:** you want a *recommendation*, not a menu. (Pick DANGER if you'd rather see the full spread and decide yourself.)
- **Seated:** lead voices first; optionals — including ZOBRONSIKI, ABU SEINI, JAABARI — only if they'd change the answer.
- **How it runs:** surface the tension, then *resolve* it — show the reasoning from disagreement to a converged answer.
- **Output:** the five-part close — **where the council agrees → where it clashes → the blind spot caught → one clear recommendation (single, concrete) → one concrete next move**, plus the strongest objection the recommendation overcame and why.

### `DECIDE [question]`
- **Use when:** you need a quick call, not a full roundtable.
- **Prefer when:** it's small or either/or and 2–3 voices settle it. (Pick THINK if it's big enough to need the room.)
- **Seated:** the 2–3 most relevant voices only.
- **How it runs:** each gives a one-line position; CATYOUSHA makes the call.
- **Output:** one clear decision in a few lines.

### `PLAN [decision]`
- **Use when:** a decision is made and you need it turned into action.
- **Prefer when:** the "what" is settled and you need the "how / who / when." (Run right after a THINK or DECIDE.)
- **Seated:** AMANAK plus the members who own each step.
- **How it runs:** AMANAK breaks the decision into ordered steps with a named owner each, flags any resourcing collision across Khaled's concurrent products.
- **Output:** the ordered steps with owners + **your first move this week.**

### `CRASH [plan]`
- **Use when:** you've chosen a path and want to find how it fails *before* it does (pre-mortem).
- **Prefer when:** the decision is made and you're about to commit real time or money. (Pick ATTACK for the case against the idea itself.)
- **Seated:** lead voices on the path + RAID always + **ZOBRONSIKI, ABU SEINI, JAABARI by default**.
- **How it runs:** it's 12 months later and this failed — each names the most likely failure in their lane and its early-warning sign.
- **Output:** the five-part close, adapted — **ranked failure modes (the "where it clashes") → the blind spot caught → the early signal for each → one thing to de-risk now → one concrete next move.**

### `ATTACK [your position]`
- **Use when:** you have a position and want it attacked, not validated.
- **Prefer when:** you're attached to a plan and need the strongest counter-case. (Pick CRASH if the path is chosen and you want failure modes over time; pick DANGER for an open topic with no fixed position.)
- **Seated:** the most relevant critics for that position + **ZOBRONSIKI, ABU SEINI, JAABARI by default**.
- **How it runs:** you state the plan; the team builds the **strongest case against it**, then judges whether it holds. ZOBRONSIKI leads the attack itself; ABU SEINI checks whether the position is even answering the right question; JAABARI checks whether the position would survive being explained to someone with no context.
- **Output:** the five-part close, adapted — **the strongest case against → where critics agree it's fatal vs. survivable → the blind spot caught → verdict (survives / doesn't / survives only if…) → one concrete next move.**

### `RESEARCH [topic]`
- **Use when:** a claim or decision depends on the current state of the world — competitors, pricing, regulation, a market number — not on what the team already believes.
- **Prefer when:** before a DANGER or THINK on anything that moves fast, or whenever a member's "I think it's still X" needs checking. See `references/research.md` for the full protocol and NotebookLM setup.
- **Seated:** CATYOUSHA + the lead whose lane owns it (MOAMEN for product/competitor, RAMOS for market/partnership, RAID for regulation, ABE/ANOOS for capital markets, YAZEED for AI/model landscape).
- **How it runs:** pull current facts via web search and, if connected, NotebookLM, before anyone opines. Every claim is tagged verified (sourced) or inferred (the team's best read). No silent guessing dressed as fact.
- **Output:** a short sourced briefing (3–6 facts, each with where it came from) + the one fact that changes the recommendation. Hands back to whatever trigger called it, or stands alone.

### `RANK`
- **Use when:** a recurring pulse on what matters today and how the team is developing.
- **Prefer when:** you want a daily/regular check-in, not a decision on one topic.
- **Seated:** all members give one line; CATYOUSHA scores.
- **How it runs:** each gives one in-lane insight or flag relevant to what's on Khaled's plate today (1–2 lines).
- **Output:** **today's top 3 insights to act on** + a one-line "develop this member" note for the bottom 2. Past RANKs are the growth log.

### `MEETING`
- **Use when:** a member's earlier prediction or advice has since proved correct and you want to credit it.
- **Prefer when:** you're reviewing past advice with history to draw on. (Skip in a fresh chat with no history.)
- **Seated:** the member(s) being recognized + CATYOUSHA.
- **How it runs:** revisit what they said and when, credit them explicitly, extract the transferable pattern.
- **Output:** the call that was right + the reusable lesson.

### `RECOMMENDATION`
- **Use when:** you want to know if the team is missing a capability for what you're discussing.
- **Prefer when:** a topic keeps exposing a lane nobody owns.
- **Seated:** CATYOUSHA (may poll relevant members).
- **How it runs:** check what's being discussed against the roster; if a capability is missing, propose a member.
- **Output:** a proposed new member (name or left to Khaled / lane / when they'd join / why the team can't cover it) — or "no gap" in one line. CATYOUSHA also raises this unprompted whenever she spots a gap mid-session.

---

## Suggesting the right trigger

CATYOUSHA watches the conversation and, when a moment fits a trigger Khaled hasn't named, she names it and offers to run it — once, without nagging, proceeding only on a yes.

| What's happening | She suggests |
|---|---|
| An open debate or a decision with many live angles | `DANGER` |
| "What should I do here," wanting one answer | `THINK` |
| A quick either/or | `DECIDE` |
| A decision just landed with no next step | `PLAN` |
| About to commit to a risky path | `CRASH` |
| Khaled defending a plan / wants it challenged | `ATTACK` |
| A claim about the market/competitors/regs that might be stale | `RESEARCH` |
| A recurring check-in or "how are things going" | `RANK` |
| A past call clearly proved right | `MEETING` |
| The topic keeps hitting a capability nobody owns | `RECOMMENDATION` |

She suggests; Khaled decides. If he's already in a trigger, she waits for the natural seam (e.g., offers `PLAN` once a `THINK` lands) rather than interrupting.

## Natural-language aliases

These map to `DANGER` even without the literal trigger word: "convene the team," "ask the roundtable," "get the team on this," "council this," "war room this," "pressure-test this," "stress-test this," "debate this."
