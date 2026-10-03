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
12. `A1_CORE_REVIEW_V1.md` — current eight-mission A1 Core editorial/static review.
13. `A1_CORE_LANGUAGE_COVERAGE_V1.md` — exact A1 word/phrase/grammar/ability grounding used across the current Core.
14. `SOURCES.md` — source hierarchy and provenance rules.
15. `BUILD_PLAN_V2.md` — current production sequence.

## Repository boundaries

This repository is for **Practice curriculum/product design** only.

- Main Learn curriculum/language inventory: `addvaluewithai-hub/english-course`
- Production app/runtime: `addvaluewithai-hub/englishlive`
- Practice authored mission source: this repository

Do not add a `Learn/` curriculum folder here. Practice may reference `english-course` item IDs for language grounding, but it does not duplicate the Learn curriculum or lesson sequence.

## Current map status

- A1 — 24 mapped missions / 8 current Core
- A2 — 24 / 8
- B1 — 24 / 8
- B2 — 24 / 8
- C1 — 21 / 7
- C2 — 21 / 7

The first complete A1–C2 map is visible. `CROSS_LEVEL_REVIEW_V1.md` records the first whole-map review and current overlap/balance risks.

The map files describe the library and progression. They are not published mission contracts.

## Current A1 production status

The current eight A1 Core missions are **content/editorially complete for the present authoring pass**.

All eight have:

- A1 grounding from `english-course`
- canonical authored dialogue
- semantic graph / accepted alternatives
- correction boundaries
- contextual Hint policy
- authored Listening Preview transcript
- adversarial QA cases

Real Gemini Live/audio QA and fixed Listening Preview audio remain publication gates.

See `A1_CORE_REVIEW_V1.md` and `A1_CORE_LANGUAGE_COVERAGE_V1.md`.

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

Do not bulk-create all mapped missions before the current Core survives empirical Live/audio QA. Repeated runtime failures should improve the factory before the library is scaled.
