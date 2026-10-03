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

## Current promoted missions

| Mission | Source file | Current stage |
| --- | --- | --- |
| A1-FS-01 — Order a drink | `a1/food-shopping/a1-food-order-drink-v1.yaml` | runtime pilot / Live QA ongoing |
| A1-EV-01 — Ask someone to repeat | `a1/everyday-life/a1-everyday-ask-repeat-v1.yaml` | contract reviewed + runtime mirror created; Live/audio QA pending |
| A1-PS-01 — Meet someone new | `a1/people-social/a1-people-meet-someone-v1.yaml` | contract reviewed; runtime promotion waits for repeat-mission QA |

`runtime pilot` is not the same as `published`. Full publication still requires the mission's QA gate, including Listening Preview audio where the level/map marks it as required.

A full mission file should be self-contained enough for review, including:

- real communicative goal
- selected language grounding from `addvaluewithai-hub/english-course`
- scenario truth
- canonical authored dialogue
- semantic conversation graph
- learner intents and accepted semantic alternatives
- preferred AI realizations where useful
- dynamic hint policy
- correction focus
- branches/recovery where useful
- Listening Preview metadata/variant where applicable
- ending conditions
- adversarial QA cases

Do not add bulk-generated catalogs here before the mission factory has passed runtime QA.

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

These references shape the authored dialogue and runtime bounds. They do **not** create a hidden checklist of items the learner must say.

See `docs/LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md` and `docs/MISSION_CONTRACT_V1.md`.
