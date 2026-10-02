# Practice Build Plan v2

Status: **current source of truth**

## Goal

Build a reviewed Practice library from a visible A1–C2 map, then promote missions into production one by one through a repeatable:

> **language grounding -> canonical dialogue -> semantic graph -> Listening variant -> bounded Live performance -> QA**

factory.

## Phase 0 — Foundation

Status: **substantially complete**.

Current foundation includes:

- level-aware Practice product shell
- A1–C2 Level Bible
- canonical World taxonomy + boundary rules
- semantic mission contract
- shared-language grounding from `english-course`
- canonical authored dialogue as a required full-mission artifact
- bounded Gemini surface freedom
- dynamic contextual Hint bundles
- optional Listening Preview design
- correction and authoring QA rules
- first live A1 vertical slice: `Order a drink`

Remaining architecture changes should be driven by real mission authoring/runtime failures, not speculative schema work.

## Phase 1 — Full Practice Map

Status: **complete first draft**.

Detailed level maps:

- A1: 24 missions / 8 Core
- A2: 24 / 8
- B1: 24 / 8
- B2: 24 / 8
- C1: 21 / 7
- C2: 21 / 7

Total: **138 candidate missions / 46 Core**.

Counts are not targets and remain editable.

See `PRACTICE_MAP_V1.md` and `practice-map/A1.md` through `C2.md`.

## Phase 2 — Cross-level review

Status: **first pass complete**.

The first review confirmed the broad progression:

```text
A1 predictable single-goal exchange
A2 routine + preference/detail/minor variation
B1 meaningful complication + explanation/problem solving
B2 trade-offs + negotiation/disagreement
C1 ambiguity + tact + register + relationship-sensitive pragmatics
C2 subtle implication + precise reformulation + layered flexibility/mediation
```

Actions already taken from review:

- narrowed `everyday-life` so it cannot become a catch-all
- clarified World boundaries
- documented duplicate/overlap watchlists
- rebalanced C1/C2 Core sets away from conflict-heavy entry experiences
- preserved conflict/negotiation missions in the wider advanced library

See `CROSS_LEVEL_REVIEW_V1.md`.

Cross-level review is not permanently “finished”: canonical-dialogue writing and Live QA may still expose weak distinctions and send missions back to the map.

## Phase 3 — Promote A1 Core missions

Status: **active production phase**.

A1 Core:

1. `A1-PS-01` — Meet someone new
2. `A1-EV-01` — Ask someone to repeat
3. `A1-FS-01` — Order a drink
4. `A1-FS-03` — Buy one item and ask the price
5. `A1-TT-01` — Ask where a place is
6. `A1-TT-03` — Check into a hotel
7. `A1-HS-02` — Book a simple appointment
8. `A1-PL-03` — Make a simple plan

`Order a drink` is already the first full vertical slice.

### Next mission

Promote **`A1-EV-01 — Ask someone to repeat`** next.

Reason: it tests a different mission family from the café transaction:

- clarification/repair
- silence/listening timing
- repeat vs slow-down requests
- confirming a recovered detail
- dynamic Hint generation after misunderstanding
- correction without turning repair into a grammar quiz

That gives better architectural evidence than immediately authoring another transaction.

### Authoring order for every promoted mission

1. validate the real communicative goal/workflow
2. inspect cumulative reviewed level language in `english-course`
3. select relevant ability/grammar/phrase/word source IDs
4. write the complete canonical dialogue
5. review dialogue for level, realism, turn length, density, and naturalness
6. define scenario truth
7. derive/validate semantic beats/branches around the dialogue
8. add preferred AI realizations and level-appropriate surface freedom
9. define correction focus and accepted semantic alternatives
10. define dynamic Hint context/anchors
11. write Listening Preview as a reviewed variant where required/useful
12. add adversarial QA cases
13. compile/sync to production runtime
14. run real Gemini Live/audio QA

## Phase 4 — A1 Core Live QA

Status: **starts mission-by-mission during Phase 3**.

Required test paths:

- canonical normal path
- valid paraphrase
- short natural response
- genuine target-relevant error
- unclear response
- silence / hesitation
- learner interruption
- Arabic help request
- dynamic Hint on expected path
- dynamic Hint after a valid detour
- impossible/unavailable option where relevant
- off-topic detour and recovery
- replay with less support
- natural ending
- surface-control check: Gemini must not make low-level normal paths harder merely for variety

When the same failure appears across missions, fix the **factory/runtime**, not each mission independently.

## Phase 5 — Complete A1 + begin A2 production

After A1 Core survives real Live QA:

- promote remaining reviewed A1 missions
- start A2 Core using the already-reviewed A2 map
- keep canonical dialogue required for every full mission
- add Listening Preview only where level policy says it materially helps

## Phase 6 — A2 / B1 production

A2 must preserve:

- one main goal + secondary detail
- preference/reason
- short connected follow-ups
- bounded variation/minor complication

B1 must add:

- meaningful complication
- connected explanation/narration
- learner-owned follow-ups
- several plausible branches
- reasonably independent problem solving

Canonical dialogue remains required while Gemini surface freedom increases.

## Phase 7 — B2 / C1 / C2 production

Increase difficulty through communication demands, not obscure vocabulary.

### B2

- competing constraints
- trade-offs
- disagreement
- counterproposals
- negotiation

### C1

- ambiguity
- register
- tact
- power/relationship sensitivity
- facilitation/reframing

### C2

- subtle implication
- precise repeated reformulation
- rapid role/register shifts
- layered mediation
- meta-communication / reframing the interaction itself

Advanced Core selections should remain balanced; do not equate advanced English with complaints and disputes.

## Phase 8 — Recommendations

After enough mission history exists, optional recommendations may use signals such as:

```text
current level
+ recent mission history
+ worlds under-practised
+ support dependence
+ observed communication needs
+ replay freshness
```

Recommendations never become a hidden mandatory path.

## Phase 9 — Custom Practice

Only after authored Practice is stable, allow runtime-generated temporary missions requested by learners.

Custom Practice must stay visibly distinct from reviewed authored missions because calibration/QA guarantees are weaker.

## Phase 10 — Free Speak

Keep Free Speak separate: open conversation without authored mission graph guarantees.

## Working rule

Before scale:

> **one mission fully grounded, deliberately written, semantically modelled, previewed where useful, and Live-tested**

is more valuable than:

> **twenty scenario prompts that leave Gemini to invent the curriculum.**

And at map level:

> **A mission title is not sacred. The progression is.**
