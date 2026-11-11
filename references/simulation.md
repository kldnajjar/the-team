# SIMULATE: crowd simulation with MiroFish

Read this when the `SIMULATE` trigger fires, or when a decision depends on **how many people would react**: a market, a customer segment, a regulator, the public, a partner ecosystem. The council gives expert opinion; a simulation gives *behavioural evidence*. Use both.

## What MiroFish is

[MiroFish](https://github.com/666ghj/MiroFish) is an open-source multi-agent prediction engine (a "swarm intelligence engine"). You give it seed material (news, a policy draft, a pricing page, a launch plan) and a prediction goal in plain language. It then:

1. builds a GraphRAG knowledge graph from the seed;
2. generates agent personas and configures them;
3. runs parallel social simulations (on the CAMEL-AI OASIS engine) with evolving memory;
4. writes a prediction report via a ReportAgent;
5. lets you interview any simulated agent or the ReportAgent afterwards.

**Stack:** Python backend + Node.js frontend, Zep Cloud memory, any OpenAI-SDK-compatible LLM. **License: AGPL-3.0.** The TEAM only *calls* a MiroFish instance you run; it doesn't bundle or modify its code.

## When to use it, and when not to

| Use SIMULATE | Don't |
|---|---|
| "How will bank buyers react to usage-based pricing?" | Questions with one factual answer (use `RESEARCH`) |
| "What happens to sentiment if we announce the enterprise tier before the competitor?" | Internal engineering choices with no crowd involved |
| "How would the partner channel respond to a direct-sales motion?" | Anything where a real customer interview is cheap and available: talk to the human |
| Stress-testing a launch message before spending on it | Personal decisions |

## How it runs

**Seated:** CATYOUSHA + the lane owner (RAMOUS for market and strategy, AMER for buyers and launch, RAID for regulator reaction, ABE for investor reaction) + **ZOBRONSIKI and JAABARI by default** to attack the result.

1. **Frame.** The lane owner writes the prediction goal in one sentence and picks 1–5 seed documents (pricing page, launch post, policy text, competitor announcement).
2. **Check cost.** Simulations are token-heavy. Start with **fewer than 40 rounds**, and confirm with Khaled before any larger run.
3. **Run.** With the MiroFish UI or API reachable (browser or HTTP tool), upload the seed, set the goal, start the run and collect the report. If it isn't reachable, offer two fallbacks and let Khaled pick: a ready-to-paste **run sheet** (seed list + goal + suggested rounds + 3 questions to ask the ReportAgent), or the **lite panel** below.
4. **Interrogate.** Ask the ReportAgent the three questions, and interview 1–2 simulated agents from the segment that matters most.
5. **Attack the result.** ZOBRONSIKI: what would make this simulation wrong (seed bias, persona skew, too few rounds)? JAABARI: would a real buyer actually behave like these agents?
6. **Close.** Tag every finding **simulated**, never *verified*.

**Output:** 3–5 simulated findings, each with how confident the team is in it → the one finding that changes the decision → the cheapest real-world check that would confirm it (one customer call, a landing-page test) → next move. Hand back to the calling trigger (`DANGER`, `THINK`, `CRASH`) or stand alone.

## Lite panel (no MiroFish needed)

A small stand-in that runs inside the TEAM, for when MiroFish isn't installed or the question doesn't justify a full run.

1. The lane owner defines 6 to 8 audience archetypes from the real segment (for example: bank CISO, procurement lead, startup CTO, regulator, reseller), each with a goal, a budget limit and a fear.
2. Each archetype reads **only the seed material**, as JAABARI does, and answers three questions: would you buy or back this, what stops you, what would change your mind. With subagents, run them in parallel; otherwise write all answers before comparing them.
3. ZOBRONSIKI and JAABARI attack the panel exactly as in step 5.
4. Tag every finding **simulated (lite)**. It is weaker evidence than a MiroFish run: no agent-to-agent interaction, no memory over time, and far fewer voices. Say so in the close.

## Setup (once)

```bash
git clone https://github.com/666ghj/MiroFish && cd MiroFish
cp .env.example .env
# set LLM_API_KEY / LLM_BASE_URL / LLM_MODEL_NAME (any OpenAI-compatible endpoint), and ZEP_API_KEY
npm run setup:all && npm run dev      # frontend :3000, backend :5001
# or: docker compose up -d
```

Requirements: Node.js 18+, Python 3.11–3.12, `uv`.

**Routing tip:** point `LLM_BASE_URL` at your LiteLLM proxy to use Bedrock, Qwen or ALLaM models under the same budget controls as the rest of your stack. Keep sensitive client seed material on a self-hosted model and in your own region.

> The MiroFish README doesn't document stable REST endpoints. Until it does, the browser UI is the supported path. If you script the backend, pin a commit.

## Integrity rules

- A simulation is a **model of a crowd, not the crowd.** It can't promote a claim to *verified*.
- Never seed it with confidential client data on a hosted LLM endpoint without the client's permission (RAID flags this).
- If the simulated result contradicts real customer evidence, the real evidence wins.
