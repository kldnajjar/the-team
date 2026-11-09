# Council protocol: modes, parallel run, decision journal

Read this for `DANGER`, `CRASH` and `ATTACK` (and `DEEP` runs), and for the journal format. Everything here works in single-pass mode too; subagents just make the independence real.

## Why

In single-pass mode one model writes every voice and has already "heard" the earlier ones, so the room drifts toward agreement. In parallel mode each voice reasons alone before seeing anyone else, then answers are judged blind. This is the same idea as Karpathy's LLM Council: independent answers → anonymous peer review → chair synthesis.

## Modes

| Mode | Fires on | Voices | Steps | Rough cost |
|---|---|---|---|---|
| **Quick** | `DECIDE`, `THINK` | 2–3 leads | frame → answers → close | 1–4 calls |
| **Standard** | `DANGER`, `CRASH`, `ATTACK` | leads + stress-testers (IDREES on `DANGER`) | all steps; debate only if consensus is high | ~10–14 calls |
| **Deep** | add `DEEP` (e.g. `DANGER DEEP: …`) or accept CATYOUSHA's escalation offer | Standard + IDREES + bench voices | all steps + debate always + options ranking + optional `SIMULATE` | 16+ calls |

CATYOUSHA offers to escalate Standard → Deep once, if council confidence comes back low. Deep never escalates further.

## Protocol

**0. Frame (CATYOUSHA).**
- **Journal lookup:** search the journal for related past decisions and inject at most 2 prior verdicts (with outcomes, if known) as context.
- **Bias audit:** one pass over the question for loaded wording, false either/or, sunk cost, or a hidden preferred answer. Flags are signals; a clean result adds nothing.
- **Brief:** at most 300 words covering decision, context, stakes, options, and the success criterion. If the question is too vague to brief, ask **one** clarifying question. Run `RESEARCH` first if facts may be stale.

**1. Independent round (parallel).** One subagent per seated voice, all spawned in a single message so they run concurrently. Each gets its card (`roster.md`), pillars (`pillars.md`), companion skills (`skills-map.md`) and the brief, and nothing from the other voices.
- **Outsider asymmetry:** JAABARI gets **only what a customer or investor would see** (copy, product names, the pitch), not the internal brief. That's what keeps his read honest.
- Answer rules: in character, in lane, deliberately one-sided, at most 150 words, ending with a **confidence block**:
  ```text
  CONFIDENCE: high | medium | low
  KEY ASSUMPTION: <the one thing this rests on>
  WOULD CHANGE MY MIND: <evidence that flips it>
  ```

**2. Anonymous peer review (parallel).** Relabel answers **A, B, C…** with names and lane words stripped, using a new random mapping every run. Each lead reviews the full set:
> *"Which answer is strongest and why? Which has the biggest blind spot? What did all of them miss? Rate overall consensus 1–5. At most 120 words. Don't guess authors."*

**3. Debate (conditional).** Take the mean consensus score.
- **≥ 4 (the room agrees):** ZOBRONSIKI prosecutes the consensus, then the top-ranked lead defends it, one turn each. High agreement is when groupthink hides, so this is where the debate pays off.
- **< 4:** skip the debate; the disagreement is already on the table.
- **Deep mode:** always debate, then rank the options, including IDREES's expanded option and any others the voices surfaced,, mark dominated options, and name what would have to be true for each survivor.

**4. Close (CATYOUSHA).** Restore names and run the merit audit against the peer rankings. Call out where a voice's confidence didn't match how peers rated it.
- **Chair may side with a lone dissenter** if the reasoning is stronger. Consensus isn't the goal; clarity is.
- **Dissent ledger:** list any strong point the recommendation softened or dropped, so it isn't lost.
- **Upside check:** if IDREES was seated, the close states whether his bigger play was adopted, deferred (with a trigger to revisit it), or rejected, and why.
- Deliver the trigger's five-part close, with a header line: `Council confidence: X · Dominant assumption: Y · Top risk: Z`.

**5. Report + log.**
- **Journal:** append the entry (below).
- **HTML report (Standard and Deep):** copy `assets/report-template.html` and replace **only** the JSON inside `<script id="council-data" type="application/json">` with this run's data (schema below). The page renders itself, with no other edits and no external assets.
  - *Claude Code:* write `the-team-report-<YYYYMMDD-HHMM>-<slug>.html` plus `…-transcript.md` (full run including the A/B/C map) in the working folder, and `open` the HTML on macOS.
  - *Claude app:* publish the filled HTML as an artifact.
  - *Quick mode / name-calls:* no report unless Khaled asks.
- Keep JSON strings plain text; the template escapes everything.

### Report data schema

```json
{
  "title": "SaaS first or self-hosted first?",
  "trigger": "DANGER", "mode": "standard", "date": "2026-11-09",
  "engine": "parallel (subagents)",
  "meta": { "confidence": "medium", "consensus": 3.2, "dominant_assumption": "…", "top_risk": "…" },
  "bias_flags": ["False either/or: both can share one image"],
  "verdict": { "recommendation": "…", "next_move": "…", "agree": ["…"], "clash": ["…"], "blind_spots": ["…"] },
  "upside": { "play": "…", "status": "deferred", "why": "…" },
  "voices": [
    { "name": "MOTASEM", "role": "Architect", "group": "build", "label": "B", "model": "claude-sonnet",
      "answer": "…", "confidence": "high", "key_assumption": "…", "would_change_mind": "…" }
  ],
  "reviews": [ { "label": "B", "rank": 1, "strongest": "…", "blind_spot": "…" } ],
  "debate": { "prosecutor": "…", "defender": "…" },
  "options": [ { "option": "…", "score": 8, "dominated": false, "must_be_true": "…" } ],
  "evidence": [ { "claim": "…", "tag": "verified", "source": "https://…" } ],
  "dissent": ["…"],
  "journal": { "id": "2026-11-09-saas-vs-helm" }
}
```

`group` is one of `chair · build · market · craft · values · stress`. `tag` is one of `verified · inferred · simulated`. `upside.status` is one of `adopted · deferred · rejected`. Omit any section that didn't happen; the page hides empty sections.

### Claude Code sketch

```text
Agent(description="TEAM: MOTASEM",    prompt="<card + pillars + skills + brief + answer rules>")
Agent(description="TEAM: JOOBOO",     prompt="...")
Agent(description="TEAM: ZOBRONSIKI", prompt="...")
Agent(description="TEAM: JAABARI",    prompt="<card + customer-facing material ONLY>")
...                                  # one message → concurrent
# then one review Agent per lead with the shuffled A/B/C set
```

No subagents? Fall back silently to single-pass and still run steps 0, 3 (as one in-thread exchange), 4 and 5.

## Optional: multi-model council

Model diversity beats persona diversity. If a LiteLLM or OpenRouter proxy is available, give voices different models: for example, leads on Claude, ZOBRONSIKI on a different vendor's model, review round on a third. Note the model next to each voice in the transcript. Keep any confidential brief on models and regions it's allowed to go to (RAID's call).

## Decision journal

Backs `MEETING`, `RANK` and step 0. Location: `.the-team/journal.jsonl` in the project, or `~/.the-team/journal.jsonl` for personal decisions (git-ignored). One JSON object per line:

```json
{"id":"2026-11-09-saas-vs-helm","date":"2026-11-09","trigger":"DANGER","mode":"standard","question":"SaaS or Helm first for ObsMate?","seated":["RAMOUS","JOOBOO","MOTASEM","ZOBRONSIKI","UNCLE SEINI","JAABARI"],"consensus":3.2,"confidence":"medium","recommendation":"SaaS first on shared abstraction; Helm one release behind","dissent":["RAMOUS: self-hosted is the entry ticket for regulated buyers"],"next_move":"List top-3 first customers and their deployment constraint","review_on":"2027-01-15","outcome":null}
```

- **Record an outcome:** `outcome <id>: <what happened>`. CATYOUSHA sets `outcome` and notes which voice called it, including any dissenter.
- **`MEETING`** credits voices whose calls proved right, using these outcomes.
- **`META`** (after 5+ entries with outcomes): CATYOUSHA reports which voices are most often right or wrong, which lanes are over- or under-used, and proposes card edits. Proposes only; Khaled decides.
- No file access (e.g. claude.ai chat)? Print the JSON line after the close so Khaled can save it.
