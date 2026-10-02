# Englotti Speaking Practice

A clean source of truth for designing **Practice** in Englotti.

> **Practice = a level-aware library of authored real-life conversations, performed dynamically by Gemini Live.**

This repository contains **Practice only**.

- Learn curriculum/language inventory: `addvaluewithai-hub/english-course`
- Production app/runtime: `addvaluewithai-hub/englishlive`
- Authored Practice design + mission source: this repository

Do not duplicate Learn curriculum here. Practice references reviewed `english-course` language for grounding, but owns its own real-life mission map and authored conversations.

## Start here

Read `docs/README.md` first. It is the canonical documentation index.

Historical/superseded docs are not kept beside current files; Git history is the archive.

## Product boundary

- **Learn** teaches English through a guided curriculum.
- **Practice** lets learners use reviewed English in authored, level-controlled real-life missions.
- **Custom Practice** may later generate temporary learner-requested scenarios with weaker calibration guarantees.
- **Free Speak** is open conversation without an authored mission blueprint.

Practice has **no mandatory linear lesson sequence**.

## Canonical authoring model

```text
Real communicative goal
  -> language grounding from english-course
  -> canonical dialogue written by Englotti
  -> semantic graph / branches
  -> Listening Preview variant
  -> bounded Gemini Live performance
  -> adversarial audio QA
```

Core principles:

> **We write the conversation. Gemini performs and adapts it.**

> **We author the intent. Gemini authors the contextual help.**

The canonical dialogue is a quality/level anchor, **not a password script**. Valid learner alternatives remain valid.

## Learner structure

```text
Practice
  -> Level
  -> World
  -> Mission
  -> optional Listening Preview
  -> Gemini Live conversation
  -> Recap / retry
```

Canonical worlds:

```text
everyday-life
people-social
food-shopping
travel-transport
work-study
home-services
plans-leisure
```

## Current curriculum status

The first complete A1–C2 Practice Map and first cross-level review are complete.

| Level | Candidate missions | Core |
| --- | ---: | ---: |
| A1 | 24 | 8 |
| A2 | 24 | 8 |
| B1 | 24 | 8 |
| B2 | 24 | 8 |
| C1 | 21 | 7 |
| C2 | 21 | 7 |
| **Total** | **138** | **46** |

Detailed maps live under `docs/practice-map/`; `docs/PRACTICE_MAP_V1.md` is the master index.

`docs/CROSS_LEVEL_REVIEW_V1.md` records the first whole-map review. It clarified World boundaries, duplicate/overlap risks, and rebalanced C1/C2 Core selections so advanced entry missions are not dominated by complaints/disputes.

The next phase is **real mission production**, not bulk YAML generation.

`Order a drink` is the first full vertical slice. The next planned Core mission is:

> **`A1-EV-01 — Ask someone to repeat`**

It intentionally tests a different interaction family: clarification/repair rather than transaction.

## Repository structure

```text
README.md

docs/
  README.md
  PRACTICE_ARCHITECTURE_V2.md
  PRACTICE_MAP_V1.md
  CROSS_LEVEL_REVIEW_V1.md
  practice-map/
    A1.md
    A2.md
    B1.md
    B2.md
    C1.md
    C2.md
  LEVEL_BIBLE_V1.md
  WORLD_TAXONOMY_V1.md
  LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md
  MISSION_CONTRACT_V1.md
  DYNAMIC_HINTS_V1.md
  LISTENING_PREVIEW_V1.md
  AUTHORING_QA_V1.md
  SOURCES.md
  BUILD_PLAN_V2.md

missions/
  README.md
  MISSION_TEMPLATE.yaml
  a1/
    ...
```

## Working rule

Do not add bulk-generated mission files just to hit a count.

> **A mission title is not sacred. The progression is.**
