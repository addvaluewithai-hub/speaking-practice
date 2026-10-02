# Practice Build Plan v2

Status: **current**

Supersedes `BUILD_PLAN_V1.md` where the two differ.

## Goal

Build a reviewed Practice library from a visible level/world map, then promote missions into production one by one through a repeatable authoring and Live-QA factory.

## Phase 0 — Current foundation

Status: substantially complete.

Current architecture includes:

- level-aware Practice product shell
- A1–C2 Level Bible
- canonical World taxonomy
- semantic mission contract
- dynamic contextual hints
- first live A1 vertical slice (`Order a drink`)
- optional Listening Preview design
- authoring / QA gates

Remaining foundation work should be driven by real authoring problems, not speculative schema expansion.

## Phase 1 — Build the library map

Status: **in progress**.

Map missions before bulk-authoring detailed contracts.

For each level define:

- primary world
- mission title
- real communicative goal
- interaction problem/shape
- Core / library status
- Listening Preview expectation

Do not design a required lesson order.

### Current order

1. A1 map + review
2. A2 map
3. B1 map
4. B2 map
5. C1 map
6. C2 map

This ordering is for authoring/review only; it is not learner progression inside Practice.

## Phase 2 — Review A1 coverage

Current A1 draft contains 24 missions across 7 worlds and 8 Core missions.

Review for:

- real usefulness
- overlap
- missing everyday interaction needs
- world balance
- interaction-shape balance
- A1 safety/predictability
- language pressure that accidentally exceeds A1

Do not keep a mission simply to hit the number 24.

## Phase 3 — Promote A1 Core missions

Promote the Core set into full authored contracts one by one.

Current Core draft:

1. Meet someone new
2. Ask someone to repeat
3. Order a drink
4. Buy one item and ask the price
5. Ask where a place is
6. Check into a hotel
7. Book a simple appointment
8. Make a simple plan

`Order a drink` is already the first runtime vertical slice.

Each promoted mission gets:

- source checks
- scenario truth
- semantic graph
- learner intents
- correction focus
- branch/recovery rules
- dynamic hint policy
- completion condition
- QA cases
- Listening Preview transcript and audio asset before full publication

## Phase 4 — Live QA the Core set

Run real voice QA, not transcript-only QA.

Required test paths include:

- normal response
- valid paraphrase
- genuine error
- short natural answer
- silence/hesitation
- dynamic Hint on expected path
- dynamic Hint after a detour
- unavailable/impossible option
- learner interruption
- Arabic help request
- off-topic detour and recovery
- replay with less support
- natural ending

Fix the mission factory when a repeated systemic problem appears. Do not patch every mission independently for the same runtime bug.

## Phase 5 — Complete the rest of A1

Once Core missions are stable, promote the remaining reviewed A1 map missions.

Not every non-Core A1 mission requires a Listening Preview, but add one where it materially helps the learner understand the interaction shape.

## Phase 6 — Map and build A2/B1

A2 must not be A1 with longer sentences.

A2 should introduce:

- one main goal plus a secondary detail
- small preferences/reasons
- short follow-up chains
- one bounded variation/minor complication

B1 should introduce:

- meaningful complications
- connected explanation
- learner-owned follow-ups
- multiple plausible branches
- more independence

Existing B1 vertical-slice research may inform runtime testing but does not dictate the new Practice map.

## Phase 7 — B2–C2

Expand only after bounded branching works reliably.

Increase:

- competing constraints
- negotiation
- trade-offs
- disagreement
- learner initiative
- discourse length
- pragmatic choices
- ambiguity
- reformulation
- register/tact

Higher-level difficulty must come from the communication problem, not obscure vocabulary.

## Phase 8 — Recommendations

After enough mission history exists, recommend missions using signals such as:

```text
current level
+ recent mission history
+ worlds under-practised
+ support dependence
+ observed communication needs
+ replay freshness
```

Recommendations remain optional and never become a hidden mandatory path.

## Phase 9 — Custom Practice

Only after authored Practice is stable, create runtime-generated temporary missions from learner requests.

Custom Practice must remain visibly different from reviewed authored missions because calibration and QA confidence are lower.

## Phase 10 — Free Speak

Keep Free Speak separate: open conversation without authored mission graph guarantees.

## Working rule

At any point, prefer:

> one mission fully sourced, authored, previewed where useful, and Live-tested

instead of:

> twenty plausible-looking mission files that have never survived a real conversation.
