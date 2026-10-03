# A1 Core editorial review v1

Status: **content/editorial pass complete; Live/audio publication QA still pending**

This review covers the current eight A1 Core / **Great place to start** missions after the Core rebalance.

Core does not mean prerequisite. It is the recommended broad starter set for A1 Practice.

## Reviewed set

| ID | Mission | World | Source contract | Editorial result |
| --- | --- | --- | --- | --- |
| A1-PS-01 | Meet someone new | People & Social | `missions/a1/people-social/a1-people-meet-someone-v1.yaml` | PASS |
| A1-EV-01 | Ask someone to repeat | Everyday Life | `missions/a1/everyday-life/a1-everyday-ask-repeat-v1.yaml` | PASS |
| A1-FS-01 | Order a drink | Food & Shopping | `missions/a1/food-shopping/a1-food-order-drink-v1.yaml` | PASS / pilot |
| A1-TT-01 | Ask where a place is | Travel & Transport | `missions/a1/travel-transport/a1-travel-ask-place-location-v1.yaml` | PASS |
| A1-TT-03 | Check into a hotel | Travel & Transport | `missions/a1/travel-transport/a1-travel-hotel-checkin-v1.yaml` | PASS |
| A1-WS-01 | Say what you do or study | Work & Study | `missions/a1/work-study/a1-work-study-say-what-you-do-v1.yaml` | PASS |
| A1-HS-02 | Book a simple appointment | Home & Services | `missions/a1/home-services/a1-services-book-simple-appointment-v1.yaml` | PASS |
| A1-PL-03 | Make a simple plan | Plans & Leisure | `missions/a1/plans-leisure/a1-plans-make-simple-plan-v1.yaml` | PASS |

`A1-FS-03 — Buy one item and ask the price` remains a fully authored **library** mission, but it is not part of the current eight-mission Core set after the balance review.

## What was checked

Every Core contract was reviewed against the current authoring factory:

```text
real communicative goal
-> A1 language grounding
-> canonical authored dialogue
-> semantic graph
-> accepted natural alternatives
-> correction boundaries
-> dynamic contextual Hint policy
-> Listening Preview variant
-> adversarial QA cases
```

The batch passes the following editorial/static gates.

### A1 level control — PASS

Across the set:

- each mission has one clear primary communication goal
- partner behaviour is collaborative and predictable
- normal-path AI turns are short
- graphs are tight and mostly linear
- short natural learner responses are explicitly accepted
- no Core mission requires extended explanation, negotiation, storytelling, or subtle register management
- difficulty comes from the communicative move, not from deliberately hard vocabulary

### Authored conversation control — PASS

All eight missions contain a reviewed `canonical_dialogue` from opening to natural ending.

The canonical dialogue controls normal-path quality, level, density and rhythm. It is not an answer password.

Every contract also describes the semantic learner intent, so natural alternatives remain valid.

### Language grounding — PASS

All eight missions reference `addvaluewithai-hub/english-course` as the shared language source of truth.

Grounding is selective rather than exhaustive: only language that materially shapes the conversation, runtime bounds, support or correction is tagged.

See `A1_CORE_LANGUAGE_COVERAGE_V1.md` for the batch inventory.

### Correction policy — PASS

The set consistently distinguishes:

- valid natural alternative -> accept
- short A1 fragment that works naturally -> accept
- genuine current English error -> concise correction/recast + useful retry when needed
- factual/task mismatch -> repair the fact/task, do not falsely call the English wrong
- unclear meaning -> clarification/repair

No mission treats canonical wording as the only correct response.

### Dynamic Hint policy — PASS

All eight Core contracts use contextual, learner-triggered support rather than hardcoded answer cards.

The intended runtime rule remains:

> first Hint tap for the active beat -> one complete generated Hint bundle -> cache -> progressive UI reveal

The authored contract supplies intent/truth/level/support anchors; Gemini writes help for the conversation that actually happened.

### Listening Preview transcript — PASS

All eight Core missions have an authored Listening Preview transcript.

Each preview is:

- optional to the learner
- orientation rather than rehearsal
- a reviewed variant rather than the exact Live script
- bounded to the same A1 interaction shape
- separate from speaking evidence

### Privacy / fictional-data boundaries — PASS

Missions that touch names, work/study, bookings, location or services explicitly allow fictional/chosen information or use authored fictional facts.

The Core set does not require real identity, contact, employer/school, payment, health-history or live-location data.

## Interaction coverage of the starter set

The eight Core missions deliberately avoid being eight versions of the same transaction.

| Interaction family | Core example |
| --- | --- |
| social opening / reciprocity | Meet someone new |
| clarification / repair | Ask someone to repeat |
| routine transaction | Order a drink |
| ask + understand location information | Ask where a place is |
| routine service check-in | Check into a hotel |
| simple self-description + reciprocal question | Say what you do or study |
| simple arrangement / option choice | Book a simple appointment |
| collaborative planning | Make a simple plan |

This is the reason `Buy one item and ask the price` was moved from Core to the wider library: it is useful, but `Order a drink` already gives the starter set a transaction and the Work & Study world needed representation.

## Source beat note

`Ask someone to repeat` contains source-only AI orchestration beats (`setup` / repeat-detail style steps) in addition to learner-response beats.

That is intentional. Production runtime compilation may collapse AI-only source beats and expose only meaningful learner-response opportunities to UI state. Source semantic structure and runtime UI state do not have to be one-to-one when no learner decision occurs between them.

## Current production/runtime state

At the time of this review:

- 8 / 8 current A1 Core missions have full source contracts
- 8 / 8 have authored Listening Preview transcripts
- 5 / 8 have already been mirrored into the current app runtime pilot set: Order a drink, Ask someone to repeat, Meet someone new, Ask where a place is, Make a simple plan
- the current runtime pilot batch has passed repository CI / Visual QA on the merged application baseline
- Check into a hotel, Say what you do or study, and Book a simple appointment remain source contracts awaiting later runtime compilation

Runtime compilation is intentionally small-batch while the app UI is being refreshed.

## Still required before publication

This editorial pass does **not** claim publication readiness.

The following remain open:

1. **Real Gemini Live/audio QA** for each Core mission, including canonical path, valid alternatives, genuine error, silence, interruption, detour/recovery and contextual Hint behaviour.
2. **Listening Preview audio assets**. All eight currently have reviewed transcripts but `audio_asset: null` until fixed audio is produced and reviewed.
3. **Runtime compilation** for the three Core contracts not yet mirrored into the app.
4. Re-open the source contract if repeated Live failures expose a factory, level or wording problem.

## Batch conclusion

The eight A1 Core missions are now considered **content/editorially complete for this authoring pass**.

The next gate is empirical performance, not more speculative schema work:

> hear them, speak through them, break them, and fix repeated runtime failures at the factory level.
