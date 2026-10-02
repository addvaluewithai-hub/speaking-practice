# Englotti Speaking Practice

A clean source of truth for designing **Practice** in Englotti.

Practice is not a second English course and not a random scenario browser.

> **Practice = a level-aware library of authored real-life conversations, performed dynamically by Gemini Live.**

## Product boundary

- **Learn** teaches English through a guided curriculum.
- **Practice** lets learners use English in authored, level-controlled real-life missions.
- **Custom Practice** lets a learner request a scenario generated at runtime.
- **Free Speak** is open conversation without an authored mission blueprint.

Practice has **no mandatory linear lesson sequence**.

Learners enter at their current level (`A1` to `C2`) and browse/replay missions by world or goal. Their current level is the default filter; other levels remain explorable rather than locked.

## Current architecture

The current product/runtime definition is:

- authored semantic conversation graphs, not fixed scripts
- mission difficulty authored at CEFR level
- Gemini performs naturally inside the graph and scenario truth
- valid alternative English is accepted
- genuine important errors receive brief correction
- dynamic contextual hints are generated from the live conversation
- the complete hint bundle is generated once per active beat and revealed progressively from cache
- optional Listening Preview can show one plausible version of the situation before the live mission
- mission completion is useful evidence from one context, not broad mastery

## Repository map

### Current documents

- `docs/PRACTICE_ARCHITECTURE_V2.md` — current product/runtime architecture
- `docs/PRACTICE_MAP_V1.md` — level/world mission library map; A1 currently drafted
- `docs/LEVEL_BIBLE_V1.md` — interaction difficulty from A1 through C2
- `docs/WORLD_TAXONOMY_V1.md` — canonical Practice worlds
- `docs/MISSION_CONTRACT_V1.md` — semantic mission contract and dynamic hint contract
- `docs/DYNAMIC_HINTS_V1.md` — live contextual hint behaviour
- `docs/LISTENING_PREVIEW_V1.md` — optional pre-mission example conversation
- `docs/AUTHORING_QA_V1.md` — mission review and Live-QA gates
- `docs/SOURCES.md` — grounding/source hierarchy
- `docs/BUILD_PLAN_V2.md` — current production plan
- `missions/` — reviewed authored mission contracts

Older versioned docs remain as historical context where a newer document explicitly supersedes them.

## Canonical learner structure

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

A1 now has a first full map of **24 candidate missions across the 7 worlds**, with **8 Core / Great place to start missions**.

Core is recommendation, not prerequisite.

The immediate production loop is:

1. review A1 map for usefulness, overlap, coverage and A1 safety
2. promote Core missions into full authored contracts
3. add Listening Previews to A1 Core missions
4. run adversarial Gemini Live/audio QA
5. complete the rest of A1
6. map A2, then B1–C2 so cross-level progression remains visible

Do not bulk-author mission files just to hit a lesson count.

## Core design rule

> **We author the intent. Gemini authors the help.**

The mission owns level, goal, truth, graph, learner intents, correction boundaries and ending conditions.

Gemini owns natural partner wording and contextual help inside those bounds.
