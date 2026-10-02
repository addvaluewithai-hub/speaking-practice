# Englotti Speaking Practice

A clean source of truth for designing **Practice** in Englotti.

> **Practice = a level-aware library of authored real-life conversations, performed dynamically by Gemini Live.**

This repository contains **Practice only**.

- Main Learn curriculum/language inventory: `addvaluewithai-hub/english-course`
- Production app/runtime: `addvaluewithai-hub/englishlive`
- Authored Practice design + mission source: this repository

Do not duplicate the Learn curriculum here. Practice references reviewed `english-course` language for grounding, but it has its own real-life mission map and authored conversations.

## Start here

Read `docs/README.md` first. It is the canonical documentation index.

Historical/superseded docs are not kept beside current files; Git history is the archive.

## Product boundary

- **Learn** teaches English through a guided curriculum.
- **Practice** lets learners use reviewed English in authored, level-controlled real-life missions.
- **Custom Practice** will allow a learner to request a runtime-generated scenario with weaker calibration guarantees.
- **Free Speak** is open conversation without an authored mission blueprint.

Practice has **no mandatory linear lesson sequence**.

Learners enter at their current level (`A1` to `C2`) and browse/replay missions by world or goal. Their current level is the default filter; other levels remain explorable rather than locked.

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

Every full authored mission therefore contains controlled language grounding, a reviewed canonical conversation, semantic intents/branches, scenario truth, correction boundaries, dynamic Hint policy, and a Listening Preview where useful/required.

The canonical dialogue is a quality and level anchor, **not a password script**. Valid learner alternatives remain valid.

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

## Current curriculum work

`docs/PRACTICE_MAP_V1.md` currently contains the first A1 map: **24 candidate missions across 7 worlds**, including **8 Core / Great place to start missions**.

Core is recommendation, not prerequisite.

Before bulk-writing detailed missions, the plan is to make the A1–C2 map visible and review cross-level progression. Reviewed map items are then promoted one by one through the grounded-dialogue authoring factory.

`Order a drink` is the first mission already promoted to the full model. Its A1 language grounding, canonical conversation, semantic graph, dynamic hints, Listening Preview variant and QA cases live together in the mission source.

## Repository structure

```text
README.md

docs/
  README.md
  PRACTICE_ARCHITECTURE_V2.md
  PRACTICE_MAP_V1.md
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

Do not add bulk-generated mission files just to hit a lesson count.
