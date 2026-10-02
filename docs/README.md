# Practice docs — start here

This directory contains the **current Practice source of truth only**.

Historical/superseded design files should not be kept beside current docs. Git history is the archive.

## Read in this order

1. `PRACTICE_ARCHITECTURE_V2.md` — what Practice is and how authored conversation + Gemini Live work together.
2. `PRACTICE_MAP_V1.md` — master index for the level/world mission library map.
3. `practice-map/A1.md` through `practice-map/C2.md` — detailed level maps.
4. `CROSS_LEVEL_REVIEW_V1.md` — first whole-map progression/overlap review.
5. `LEVEL_BIBLE_V1.md` — what interaction difficulty means from A1 to C2.
6. `WORLD_TAXONOMY_V1.md` — canonical browsing worlds and boundary rules.
7. `LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md` — how reviewed `english-course` language becomes an authored Practice conversation.
8. `MISSION_CONTRACT_V1.md` — the full mission object/schema.
9. `DYNAMIC_HINTS_V1.md` — contextual Hint generation and caching.
10. `LISTENING_PREVIEW_V1.md` — optional reviewed example conversation before Live Practice.
11. `AUTHORING_QA_V1.md` — review and publication gates.
12. `SOURCES.md` — source hierarchy and provenance rules.
13. `BUILD_PLAN_V2.md` — current production sequence.

## Repository boundaries

This repository is for **Practice curriculum/product design** only.

- Main Learn curriculum/language inventory: `addvaluewithai-hub/english-course`
- Production app/runtime: `addvaluewithai-hub/englishlive`
- Practice authored mission source: this repository

Do not add a `Learn/` curriculum folder here. Practice may reference `english-course` item IDs for language grounding, but it does not duplicate the Learn curriculum or lesson sequence.

## Current map status

- A1 — first full map drafted: `practice-map/A1.md`
- A2 — first full map drafted: `practice-map/A2.md`
- B1 — first full map drafted: `practice-map/B1.md`
- B2 — first full map drafted: `practice-map/B2.md`
- C1 — first full map drafted: `practice-map/C1.md`
- C2 — first full map drafted: `practice-map/C2.md`

The first complete A1–C2 map is visible. `CROSS_LEVEL_REVIEW_V1.md` records the first whole-map review and current overlap/balance risks.

The map files describe the library and progression. They are not published mission contracts.

## Current authoring rule

```text
real communicative goal
-> language grounding from english-course
-> canonical dialogue written by Englotti
-> semantic graph / branches
-> Listening Preview variant
-> bounded Gemini Live performance
-> adversarial Live QA
```

> **We write the conversation. Gemini performs and adapts it.**

> **We author the intent. Gemini authors the contextual help.**

## Mission files

Detailed authored missions live in `../missions/`.

Use `../missions/MISSION_TEMPLATE.yaml` when promoting a reviewed Practice Map item into a full mission contract.

Current production guidance after the whole-map draft: do **not** bulk-create all mapped missions. Promote reviewed Core missions one by one so real dialogue authoring and Live QA can still change the factory/map when needed.
