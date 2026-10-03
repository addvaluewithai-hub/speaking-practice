# Authored Missions

This folder contains reviewed Practice missions promoted from the level maps into full authoring contracts.

Suggested layout:

```text
missions/
  a1/
    everyday-life/
    people-social/
    food-shopping/
    travel-transport/
    home-services/
    work-study/
    plans-leisure/
  a2/
  b1/
  b2/
  c1/
  c2/
```

## Current A1 Core

The current eight A1 Core / **Great place to start** missions all have full source contracts and have completed the current content/editorial review pass.

| Mission | Source file | Current stage |
| --- | --- | --- |
| A1-PS-01 — Meet someone new | `a1/people-social/a1-people-meet-someone-v1.yaml` | editorial pass + runtime mirror; Live/audio QA pending |
| A1-EV-01 — Ask someone to repeat | `a1/everyday-life/a1-everyday-ask-repeat-v1.yaml` | editorial pass + runtime mirror; Live/audio QA pending |
| A1-FS-01 — Order a drink | `a1/food-shopping/a1-food-order-drink-v1.yaml` | editorial pass + runtime pilot; Live/audio QA ongoing |
| A1-TT-01 — Ask where a place is | `a1/travel-transport/a1-travel-ask-place-location-v1.yaml` | editorial pass + runtime mirror; Live/audio QA pending |
| A1-TT-03 — Check into a hotel | `a1/travel-transport/a1-travel-hotel-checkin-v1.yaml` | editorial pass; runtime compilation pending |
| A1-WS-01 — Say what you do or study | `a1/work-study/a1-work-study-say-what-you-do-v1.yaml` | editorial pass; runtime compilation pending |
| A1-HS-02 — Book a simple appointment | `a1/home-services/a1-services-book-simple-appointment-v1.yaml` | editorial pass; runtime compilation pending |
| A1-PL-03 — Make a simple plan | `a1/plans-leisure/a1-plans-make-simple-plan-v1.yaml` | editorial pass + runtime mirror; Live/audio QA pending |

See:

- `../docs/A1_CORE_REVIEW_V1.md` — batch editorial/QA review
- `../docs/A1_CORE_LANGUAGE_COVERAGE_V1.md` — exact A1 word/phrase/grammar/ability grounding counts

## Additional authored A1 library mission

`A1-FS-03 — Buy one item and ask the price` is also a complete reviewed source contract:

`a1/food-shopping/a1-food-buy-one-item-price-v1.yaml`

It was deliberately moved out of Core after the starter-set balance review because `Order a drink` already supplies a transaction and the Core needed Work & Study representation. It remains part of the wider A1 library.

## Publication status

`editorial pass`, `runtime mirror`, `pilot`, and `published` are different states.

A mission is not published merely because its source contract exists or repository CI passes.

For A1 Core, full publication still requires:

- real Gemini Live/audio QA
- fixed/reviewed Listening Preview audio
- successful runtime compilation where not already mirrored
- re-review if Live behaviour exposes a source/factory problem

## Full mission contents

A full mission should be self-contained enough for review, including:

- real communicative goal
- selected language grounding from `addvaluewithai-hub/english-course`
- scenario truth
- canonical authored dialogue
- semantic conversation graph
- learner intents and accepted semantic alternatives
- preferred AI realizations where useful
- dynamic contextual Hint policy
- correction focus
- branches/recovery where useful
- Listening Preview metadata/variant where applicable
- ending conditions
- adversarial QA cases

Do not bulk-generate the mapped library into contracts before the factory has survived real Live QA.

## Naming

Prefer stable semantic IDs, for example:

```text
a1-food-order-drink-v1.yaml
b1-travel-change-hotel-booking-v1.yaml
```

A revised mission should preserve identity and advance `revision` rather than silently changing learner expectations/content.

## Conversation authoring rule

**Write the conversation, then describe its semantics.**

Every full mission needs a reviewed `canonical_dialogue`: one plausible level-safe path from opening to ending.

Then author what each turn is **doing** so Gemini can adapt without turning the reference dialogue into a password script.

Good combination:

```text
canonical learner line:
Do you have a table outside?

learner_intent:
ask whether an outside table is available
```

Bad runtime requirement:

```text
required_text: Do you have a table outside?
```

The canonical line controls quality/level. The semantic intent controls acceptance.

Valid alternatives remain valid.

## Language grounding rule

Use reviewed language selectively and naturally.

The mission may reference relevant:

- abilities
- grammar
- phrases
- words
- pronunciation/performance constraints

These references shape authored dialogue, support and runtime bounds. They do **not** create a hidden checklist of items the learner must say.

See `../docs/LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md` and `../docs/MISSION_CONTRACT_V1.md`.
