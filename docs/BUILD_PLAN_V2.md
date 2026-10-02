# Practice Build Plan v2

Status: **current**

Supersedes `BUILD_PLAN_V1.md` where the two differ.

## Goal

Build a reviewed Practice library from a visible A1–C2 level/world map, then promote missions into production one by one through a repeatable **language-grounded dialogue authoring + semantic graph + Live-QA** factory.

## Phase 0 — Current foundation

Status: substantially complete.

Current architecture includes:

- level-aware Practice product shell
- A1–C2 Level Bible
- canonical World taxonomy
- Practice Map approach
- shared-language grounding from `english-course`
- canonical authored dialogue as a required full-mission artifact
- semantic mission graph
- bounded Gemini surface freedom
- dynamic contextual hints
- first live A1 vertical slice (`Order a drink`)
- optional Listening Preview design
- authoring / QA gates

Remaining foundation work should be driven by real authoring problems, not speculative schema expansion.

## Phase 1 — Build the full library map

Status: **in progress**.

Map A1–C2 before bulk-authoring detailed mission contracts.

For each level define:

- primary world
- mission title
- real communicative goal
- interaction problem/shape
- Core / library status
- Listening Preview expectation

Do not design a required lesson order.

### Mapping order

1. A1 map + review
2. A2 map
3. B1 map
4. B2 map
5. C1 map
6. C2 map

This ordering is for authoring/review only; it is not learner progression inside Practice.

### Why map all levels first

Seeing the full map before bulk implementation lets us catch:

- repeated missions pretending to be progression
- A2/B1 missions that are only A1 with longer sentences
- gaps in real-life coverage
- worlds that disappear at certain levels without a reason
- difficulty jumps that are too large or too small
- higher-level missions that rely on obscure vocabulary instead of a harder communication problem

The existing `Order a drink` pilot remains useful runtime research while the map is completed.

## Phase 2 — Cross-level map review

After A1–C2 titles/goals are visible, review the whole library for progression.

Questions:

- Does the communication problem genuinely evolve across levels?
- Are the same real-life worlds revisited in richer ways where useful?
- Are some missions duplicates under different names?
- Does each level have a balanced mix of social, information, service, planning, repair, problem-solving and higher-level interaction needs?
- Are Core missions a helpful entry set rather than a hidden sequence?

Mission count is a result of coverage quality, not a target.

## Phase 3 — Promote A1 Core missions

Promote the reviewed A1 Core set into full authored contracts one by one.

Current draft Core set:

1. Meet someone new
2. Ask someone to repeat
3. Order a drink
4. Buy one item and ask the price
5. Ask where a place is
6. Check into a hotel
7. Book a simple appointment
8. Make a simple plan

`Order a drink` is already the first runtime vertical slice and first mission upgraded to the grounded-dialogue model.

### Authoring order for every promoted mission

1. validate the real communicative goal/workflow
2. select relevant reviewed language from `english-course`
3. write the complete canonical dialogue
4. review the dialogue for level, realism, turn length and language coverage
5. author/validate the semantic graph around the dialogue
6. add preferred AI realizations and surface-freedom bounds
7. write the Listening Preview as a reviewed variant where required/useful
8. define correction focus, dynamic-hint context and completion conditions
9. add adversarial QA cases
10. compile into the production runtime and test Live

Each promoted mission therefore gets:

- source checks
- language grounding references
- canonical authored dialogue
- scenario truth
- semantic graph
- learner intents
- preferred AI realizations where useful
- correction focus
- branch/recovery rules
- dynamic hint policy
- completion condition
- QA cases
- Listening Preview transcript and audio asset before full publication when required

See `LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md`.

## Phase 4 — Live QA the A1 Core set

Run real voice QA, not transcript-only QA.

Required test paths include:

- canonical normal path
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
- surface-control check: Gemini should not make a low-level normal path harder merely for stylistic variety

Fix the mission factory when a repeated systemic problem appears. Do not patch every mission independently for the same runtime bug.

## Phase 5 — Complete A1 and start A2 production

Once the Core missions are stable:

- promote the remaining reviewed A1 missions
- begin A2 Core production using the already-reviewed cross-level map

Not every non-Core mission requires a Listening Preview. Add one where it materially helps the learner understand the interaction shape.

Every full mission still requires an authored canonical dialogue even when no Listening Preview is included.

## Phase 6 — A2 and B1 production

A2 must introduce more than longer sentences:

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

At A2/B1, canonical dialogues remain required, but Gemini's allowed surface variation and authored branching can increase.

Existing B1 vertical-slice research may inform runtime testing but does not dictate the Practice map.

## Phase 7 — B2–C2 production

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

Canonical conversation/branch exemplars still matter at higher levels, but runtime surface freedom becomes wider inside authored truth, goals and pragmatic constraints.

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

Before bulk production, prefer a **complete visible map with honest gaps** over dozens of detailed mission files that accidentally lock us into the wrong curriculum shape.

After the map is approved, prefer:

> one mission with reviewed language grounding, a deliberately written canonical conversation, a semantic graph, bounded Live behaviour, a useful preview where appropriate, and real audio QA

instead of:

> twenty scenario prompts that leave Gemini to invent the curriculum at runtime.
