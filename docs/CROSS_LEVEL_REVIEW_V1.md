# Practice Cross-Level Review v1

Status: **first whole-map review complete**

Scope: `docs/practice-map/A1.md` through `C2.md`.

This review tests whether the complete library behaves like a coherent progression rather than six unrelated scenario lists.

## 1. Current map size

| Level | Candidate missions | Core |
| --- | ---: | ---: |
| A1 | 24 | 8 |
| A2 | 24 | 8 |
| B1 | 24 | 8 |
| B2 | 24 | 8 |
| C1 | 21 | 7 |
| C2 | 21 | 7 |
| **Total** | **138** | **46** |

Counts are descriptive, not targets. Missions may still be removed, merged, or replaced after canonical-dialogue authoring and Live QA.

## 2. Progression result

The first full map has a usable interaction progression:

```text
A1  predictable single-goal exchange
A2  routine exchange + preference/detail/minor variation
B1  meaningful complication + connected explanation/problem solving
B2  competing constraints + trade-offs + disagreement/negotiation
C1  ambiguity + tact + register + relationship-sensitive pragmatics
C2  subtle implication + precise reformulation + layered mediation/flexibility
```

This is materially different from increasing sentence length or vocabulary difficulty.

## 3. Strong mission families worth preserving

### Request / food-service

```text
A1 order one item
-> A2 order with preferences / ask about options
-> B1 resolve a wrong order
-> B2 negotiate when the straightforward correction is unavailable
-> C1 handle a significant complaint with tact / ambiguous expectations
-> C2 manage fine distinctions, policy/fairness/face, and precise reformulation
```

### Clarification / misunderstanding

```text
A1 ask for repetition
-> A2 identify the unclear detail
-> B1 explain and repair an actual misunderstanding
-> B2 manage conflicting accounts / active factual disagreement
-> C1 separate fact from assumption under ambiguity and relationship risk
-> C2 preserve several nuanced interpretations while reframing dynamically
```

### Travel

```text
A1 locate / ticket / straightforward check-in
-> A2 route clarification / simple booking change
-> B1 disruption / unavailable requested change
-> B2 rebook under meaningful trade-offs
-> C1 ambiguous responsibility / audience adaptation / diplomatic escalation
-> C2 coordinate multiple providers, frames, and authority levels
```

### Plans / arrangements

```text
A1 make a simple plan
-> A2 preference/reason + one alternative
-> B1 re-plan after one meaningful complication
-> B2 balance explicit competing preferences/constraints
-> C1 manage partly implicit social priorities
-> C2 redesign the decision/communication frame itself
```

### Service problem

```text
A1 state visible problem + ask for help
-> A2 describe details + arrange next step
-> B1 explain history/recurrence + solve
-> B2 negotiate responsibility/cost/time after failed service
-> C1 escalate tactfully / manage uncertain causation
-> C2 coordinate multiple responsibility frames and ambiguous commitments
```

## 4. World taxonomy decisions

The review exposed useful boundaries, now recorded in `WORLD_TAXONOMY_V1.md`.

### Everyday Life

Keep it, but it is **not a catch-all**. A mission belongs there only when its value is genuinely cross-context and no other World is more natural.

### Food & Shopping vs Home & Services

- `food-shopping` = discrete purchase/order/product transaction
- `home-services` = ongoing provider/service/appointment/repair/subscription relationship

### People & Social vs Plans & Leisure

- `people-social` = the relationship/conversation itself is the goal
- `plans-leisure` = deciding/organising/repairing an activity or event is the goal

### Work & Study

Higher-level first drafts leaned professional. During full mission production, deliberately vary workplace and study/academic truth models where the communication problem genuinely transfers. Do not duplicate every mission merely to produce both versions.

## 5. Advanced Core balance — resolved in this review

The first C1/C2 Core selections were too conflict-heavy. The **library itself was not the problem**; advanced learners genuinely need complaint, disagreement, negotiation, and mediation. The problem was the entry/recommendation set implying that advanced English mainly means conflict management.

### Revised C1 Core

- `C1-EV-03` — audience/register adaptation
- `C1-PS-02` — indirect concern / tactful clarification
- `C1-FS-01` — diplomatic service complaint
- `C1-TT-02` — complex requirement across staff roles
- `C1-WS-03` — meeting facilitation / synthesis
- `C1-HS-03` — reformulate complex service requirements
- `C1-PL-02` — implicit priorities in collaborative planning

### Revised C2 Core

- `C2-EV-02` — rapid audience adaptation / precise reformulation
- `C2-PS-02` — shifting tone / implication
- `C2-FS-03` — preserve fine distinctions while negotiating
- `C2-TT-02` — role/register shifts across authority levels
- `C2-WS-01` — one deliberate layered-mediation Core
- `C2-HS-02` — strategic ambiguity / precise commitments
- `C2-PL-03` — meta-communication / style mediation

Result: advanced Core now demonstrates a broader sample of C1/C2 capability while conflict-heavy missions remain available in the full library.

## 6. Duplicate / overlap watchlist

Authoring must preserve these distinctions:

- A2 personal routine vs A2 work/study responsibilities
- B1 discrete product/service complaint vs B1 ongoing delayed-service follow-up
- B2 one-off disputed purchase charge vs B2 ongoing subscription/provider billing dispute
- C1 discrete service complaint vs C1 persistent provider escalation
- C2 multi-party travel/home/professional mediation must not become the same graph with different nouns

**Rule:** if canonical-dialogue authoring produces nearly the same roles, truth, graph, and learner moves with only surface nouns changed, merge or replace one mission.

## 7. Conflict-density rule for higher levels

B2–C2 naturally contain more disagreement and negotiation because those create authentic communication pressure.

But every high-level World should also include difficulty driven by non-conflict skills such as:

- complex explanation
- audience/register adaptation
- facilitation
- indirect meaning
- precise reformulation
- ambiguity management
- synthesis

The revised C1/C2 Core sets now model this rule.

## 8. Listening Preview review

Current policy remains appropriate:

- A1 Core: required content asset before full publication; learner may skip
- A2 Core: recommended
- B1: selective
- B2: selective/rare
- C1: selective when pragmatic modelling adds value
- C2: rare

High-level previews must not remove the ambiguity/unpredictability that defines the mission.

## 9. Language-grounding review

Do **not** pre-tag all 138 mapped missions with full vocabulary/grammar metadata.

Mission-specific grounding happens when a mission is promoted:

```text
real communicative goal
-> select relevant cumulative language inventory
-> write canonical dialogue
-> record only source items that materially shaped language, level, correction, or support
```

This keeps language grounding useful rather than turning metadata into a second curriculum.

## 10. Production decision

The mapping phase and first cross-level review are complete enough to resume real mission production.

Do not bulk-create 138 YAML files.

Next production loop:

1. promote one A1 Core mission
2. ground it in `english-course`
3. write the canonical dialogue
4. derive/validate the semantic graph
5. author its Listening Preview variant
6. define correction + dynamic Hint boundaries
7. run adversarial Gemini Live/audio QA
8. change the factory/map if real implementation exposes a systemic problem

`Order a drink` is the first completed vertical slice.

Recommended next mission: **`A1-EV-01 — Ask someone to repeat`**, because it tests a different interaction family: clarification/repair instead of transaction.

## 11. Whole-map principle

> **A mission title is not sacred. The progression is.**

If real authored dialogue or Gemini Live QA shows that two missions collapse into the same conversation, change the map rather than forcing implementation to preserve a weak distinction.
