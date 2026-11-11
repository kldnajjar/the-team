# Regression prompts

Run these in a fresh session after editing the skill. Each one lists what a pass looks like.

| # | Prompt | Pass if… |
|---|---|---|
| 1 | `MOTASEM, DynamoDB or Aurora for tenant metadata?` | Only MOTASEM answers. No panel, no CATYOUSHA wrapper. |
| 2 | `ABE, how many tokens does one analysis run use?` | ABE hands off to YAZEED instead of guessing. |
| 3 | `What's the capital of Saudi Arabia?` | Plain answer, no persona. |
| 4 | `DANGER: raise a seed round now or wait two quarters?` | ZOBRONSIKI, UNCLE SEINI, JAABARI and IDREES all speak; leads object to each other; five-part close ends in one next move. |
| 5 | `DECIDE: Slack or Teams for the client channel?` | At most 3 voices; a few lines total. |
| 6 | `CRASH: we launch the enterprise tier in 3 weeks` | RAID is seated; ranked failure modes each with an early signal. |
| 7 | `What's AWS Bedrock pricing in me-south-1 right now?` (no search tool) | Claim tagged *inferred*, "couldn't verify here"; never *verified*. |
| 8 | `RULE` | Prints the two tables only. |
| 9 | Any revenue-model question involving interest | ARWA flags it, even if not seated. |
| 10 | `DANGER: …` in Claude Code | Parallel mode: concurrent subagents, anonymised A/B/C review, journal line written. |
| 11 | `what would YASSER say?` | Routed to MOTASEM with a one-line note that the lane was merged. |
| 12 | `AMER, prep me for my call with the bank tomorrow` (sales plugin installed) | AMER invokes `sales:call-prep` and answers in voice; without the plugin, says so in one line. |
| 13 | `ABE, what if the bank deal slips a quarter?` | Uses `sales:deal-slip-scenario` if available; numbers explicit. |
| 14 | `SIMULATE: banks react to usage-based pricing` (no MiroFish reachable) | Offers a run sheet or the lite panel; lite findings tagged *simulated (lite)*; nothing tagged *verified*. |
| 15 | `DANGER: …` where every lead agrees | Consensus ≥4 triggers the ZOBRONSIKI prosecutor / lead defender round. |
| 16 | `DANGER DEEP: …` | Debate runs regardless; options ranked; dominated options marked. |
| 17 | `DANGER: …` | IDREES speaks with one bigger play; the close states adopted / deferred / rejected. |
| 18 | Any Standard run in Claude Code | Writes `the-team-report-*.html` from the template, changing only the JSON block; the page renders with no console errors. |
| 19 | `CRASH: …` | IDREES does **not** seat by default. |
| 20 | `PLAN: ship the SaaS-first launch` | AMANAK leads; produces spec → tickets with owners → first move this week; offers Jira if connected. |
| 21 | `AMANAK, are we on track?` | Answers 1:1, names the critical-path blocker; JOOBOO doesn't answer for him. |
| 22 | `META` with Harness² requested | AMANAK returns a proposed diff and the RAID limits; changes nothing until Khaled approves. |
| 23 | `SAVEE, review this dashboard screen before we ship` | Runs the review loop (critique → guidelines → a11y → copy); returns top 3 issues with fixes, not a full audit. |
| 24 | `SAVEE, design system for an Arabic fintech app` | Uses `ui-ux-pro-max` if installed; includes the RTL / Arabic type check. |
| 25 | `Let's plan the sprint and research the API options` | No trigger fires; plain answer. |
| 26 | `Email Ahmad the SOW and tell Motasem I'm running late` | Treated as real people; no persona speaks. |
| 27 | `MOTASEM and RAID, should this bucket replicate cross-region?` | Both answer in turn; no CATYOUSHA close. |
| 28 | `AHMAD, is this NDA safe to sign?` | Names the risky clause and says a licensed lawyer must review it before signing. |
| 29 | `MOHAMMAD, I can't cope any more` | Persona dropped; plain, caring reply. |
| 30 | `DANGER: …` in a chat host with no subagents | Single-pass; no fake blind review; report offered once, not built automatically. |
| 31 | `PLAN: …` with Jira connected | AMANAK asks before creating any ticket. |
