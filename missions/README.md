# Authored Missions

This folder contains reviewed Practice missions.

Suggested layout:

```text
missions/
  a1/
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

A mission file should be self-contained enough for review: goal, scenario truth, conversation graph, learner intents, hints, correction focus, branches, and ending conditions.

Do not add bulk-generated catalogs here before the vertical-slice missions have passed runtime QA.

## Naming

Prefer stable semantic IDs, for example:

```text
a1-food-order-drink-v1.yaml
b1-travel-change-hotel-booking-v1.yaml
```

A revised mission should preserve identity and advance revision rather than silently changing learner expectations.

## Conversation authoring rule

Author **what each turn is doing**, not one password sentence the learner must repeat.

Good:

```text
learner_intent: ask whether an outside table is available
```

Bad:

```text
required_text: Do you have a table outside?
```

Full-answer hints may contain natural example sentences, but valid alternatives remain valid.
