# Practice docs — start here

This directory contains the **current Practice source of truth only**.

Historical/superseded design files should not be kept beside current docs. Git history is the archive.

## Read in this order

1. `PRACTICE_ARCHITECTURE_V2.md` — what Practice is and how authored conversation + Gemini Live work together.
2. `PRACTICE_MAP_V1.md` — master index for the level/world mission library map.
3. `practice-map/A1.md`, `practice-map/A2.md`, ... — detailed level maps as they are drafted.
4. `LEVEL_BIBLE_V1.md` — what interaction difficulty means from A1 to C2.
5. `WORLD_TAXONOMY_V1.md` — the canonical browsing worlds.
6. `LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md` — how reviewed `english-course` language becomes an authored Practice conversation.
7. `MISSION_CONTRACT_V1.md` — the full mission object/schema.
8. `DYNAMIC_HINTS_V1.md` — contextual Hint generation and caching.
9. `LISTENING_PREVIEW_V1.md` — optional reviewed example conversation before Live Practice.
10. `AUTHORING_QA_V1.md` — review and publication gates.
11. `SOURCES.md` — source hierarchy and provenance rules.
12. `BUILD_PLAN_V2.md` — current production sequence.

## Repository boundaries

This repository is for **Practice curriculum/product design** only.

- Main Learn curriculum/language inventory: `addvaluewithai-hub/english-course`
- Production app/runtime: `addvaluewithai-hub/englishlive`
- Practice authored mission source: this repository

Do not add a `Learn/` curriculum folder here. Practice may reference `english-course` item IDs for language grounding, but it does not duplicate the Learn curriculum or lesson sequence.

## Current map status

- A1 — first full map drafted: `practice-map/A1.md`
- A2 — first full map drafted: `practice-map/A2.md`
- B1 — next mapping pass
- B2/C1/C2 — pending

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
