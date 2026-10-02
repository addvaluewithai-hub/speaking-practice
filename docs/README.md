# Practice docs — start here

This directory contains the **current Practice source of truth only**.

Historical/superseded design files should not be kept beside current docs. Git history is the archive.

## Read in this order

1. `PRACTICE_ARCHITECTURE_V2.md` — what Practice is and how authored conversation + Gemini Live work together.
2. `PRACTICE_MAP_V1.md` — the level/world mission library map. This is the curriculum map, not a linear lesson sequence.
3. `LEVEL_BIBLE_V1.md` — what interaction difficulty means from A1 to C2.
4. `WORLD_TAXONOMY_V1.md` — the canonical browsing worlds.
5. `LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md` — how reviewed `english-course` language becomes an authored Practice conversation.
6. `MISSION_CONTRACT_V1.md` — the full mission object/schema.
7. `DYNAMIC_HINTS_V1.md` — contextual Hint generation and caching.
8. `LISTENING_PREVIEW_V1.md` — optional reviewed example conversation before Live Practice.
9. `AUTHORING_QA_V1.md` — review and publication gates.
10. `SOURCES.md` — source hierarchy and provenance rules.
11. `BUILD_PLAN_V2.md` — current production sequence.

## Repository boundaries

This repository is for **Practice curriculum/product design** only.

- Main Learn curriculum/language inventory: `addvaluewithai-hub/english-course`
- Production app/runtime: `addvaluewithai-hub/englishlive`
- Practice authored mission source: this repository

Do not add a `Learn/` curriculum folder here. Practice may reference `english-course` item IDs for language grounding, but it does not duplicate the Learn curriculum or lesson sequence.

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
