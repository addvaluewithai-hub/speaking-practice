# Practice Build Plan v2

Status: **current source of truth**

## Goal

Build a reviewed Practice library from a visible A1–C2 map, then promote missions through a repeatable:

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
- mission-generic authored Practice Live runtime

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

The broad progression is:

```text
A1 predictable single-goal exchange
A2 routine + preference/detail/minor variation
B1 meaningful complication + explanation/problem solving
B2 trade-offs + negotiation/disagreement
C1 ambiguity + tact + register + relationship-sensitive pragmatics
C2 subtle implication + precise reformulation + layered flexibility/mediation
```

Actions already taken include World-boundary cleanup, overlap watchlists, and advanced-Core rebalancing.

See `CROSS_LEVEL_REVIEW_V1.md`.

## Phase 3 — A1 Core source production

Status: **content/editorial pass complete for all eight current Core missions**.

Current A1 Core:

1. `A1-PS-01` — Meet someone new
2. `A1-EV-01` — Ask someone to repeat
3. `A1-FS-01` — Order a drink
4. `A1-TT-01` — Ask where a place is
5. `A1-TT-03` — Check into a hotel
6. `A1-WS-01` — Say what you do or study
7. `A1-HS-02` — Book a simple appointment
8. `A1-PL-03` — Make a simple plan

All eight now have:

- selected A1 grounding from `english-course`
- authored canonical dialogue
- semantic conversation graph
- accepted natural alternatives
- correction boundaries
- dynamic contextual Hint policy
- authored Listening Preview transcript
- adversarial QA cases

See:

- `A1_CORE_REVIEW_V1.md`
- `A1_CORE_LANGUAGE_COVERAGE_V1.md`
- `missions/README.md`

`A1-FS-03 — Buy one item and ask the price` is also fully authored but remains a wider-library mission rather than Core after starter-set balancing.

### Runtime pilot set

Five Core missions have already been mirrored into the application runtime:

- transaction: `Order a drink`
- clarification/repair: `Ask someone to repeat`
- social opening: `Meet someone new`
- directions/location: `Ask where a place is`
- collaborative planning: `Make a simple plan`

The remaining three source contracts are deliberately not being bulk-compiled while the application UI is being refreshed:

- `Check into a hotel`
- `Say what you do or study`
- `Book a simple appointment`

Source work can continue independently in `speaking-practice`; app compilation should remain small-batch and coordinated with the runtime/UI baseline.

## Phase 4 — A1 Core empirical Live/audio QA

Status: **next active gate**.

Editorial completion is not publication.

Every Core mission still needs real Gemini Live/audio testing across:

- canonical normal path
- valid paraphrase
- short natural response
- genuine target-relevant error -> concise correction + retry
- unclear response
- factual/task mismatch
- silence / hesitation
- learner interruption
- Arabic help request
- dynamic Hint on expected path
- dynamic Hint after a valid detour
- impossible/unavailable option where relevant
- off-topic detour and recovery
- replay with less support
- natural ending
- surface-control check: Gemini must not make A1 harder merely for variety

When the same failure appears across missions, fix the **factory/runtime**, not each mission independently.

### Listening Preview audio gate

All eight current Core missions have reviewed preview transcripts, but fixed audio still needs to be produced/reviewed before publication.

The publication distinction stays explicit:

```text
source contract complete
!= repository CI passed
!= Live/audio QA passed
!= published
```

## Phase 5 — Complete A1 library + start A2 Core

Start this only after the Core batch provides enough real Live evidence that the factory is stable.

Then:

- author/promote the remaining A1 library missions from the 24-mission map
- retain `Buy one item and ask the price` as an already-authored library mission
- start A2 Core from the reviewed A2 map
- keep canonical dialogue required for every full mission
- use Listening Preview where level policy says it materially helps

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

After enough mission history exists, optional recommendations may use:

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

Custom Practice stays visibly distinct because calibration/QA guarantees are weaker.

## Phase 10 — Free Speak

Keep Free Speak separate: open conversation without authored mission graph guarantees.

## Authoring order for future missions

1. validate the real communicative goal/workflow
2. inspect cumulative reviewed level language in `english-course`
3. select relevant ability/grammar/phrase/word source IDs
4. write the complete canonical dialogue
5. review level, realism, turn length, density and naturalness
6. define scenario truth
7. derive/validate semantic beats and branches
8. add preferred AI realizations and level-appropriate surface freedom
9. define correction focus and accepted semantic alternatives
10. define dynamic Hint context/anchors
11. write Listening Preview variant where required/useful
12. add adversarial QA cases
13. compile/sync to production runtime
14. run repository CI/Visual QA
15. run real Gemini Live/audio QA

## Working rule

Before scale:

> **one mission fully grounded, deliberately written, semantically modelled, previewed where useful, and Live-tested**

is more valuable than:

> **twenty scenario prompts that leave Gemini to invent the curriculum.**

And at map level:

> **A mission title is not sacred. The progression is.**
