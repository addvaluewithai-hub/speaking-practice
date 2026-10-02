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

- Practice missions are written by us, not invented fresh by Gemini
- each full mission selects relevant reviewed language from `addvaluewithai-hub/english-course`
- each full mission contains a **canonical authored dialogue** from opening to natural ending
- the canonical dialogue is then represented as a semantic graph for adaptation/branching
- Gemini performs/adapts the authored conversation inside scenario truth, level bounds and graph constraints
- lower levels stay much closer to reviewed canonical/preferred wording; higher levels allow more surface freedom
- valid alternative learner English is accepted; the canonical dialogue is not a password script
- genuine important errors receive brief correction
- dynamic contextual hints are generated from the live conversation, using grounded/canonical language as support anchors rather than hardcoded answers
- the complete hint bundle is generated once per active beat and revealed progressively from cache
- optional Listening Preview is a reviewed variant of the same authored interaction/language grounding
- mission completion is useful evidence from one context, not broad mastery

## Repository map

### Current documents

- `docs/PRACTICE_ARCHITECTURE_V2.md` — current product/runtime architecture
- `docs/PRACTICE_MAP_V1.md` — level/world mission library map; A1 currently drafted
- `docs/LEVEL_BIBLE_V1.md` — interaction difficulty from A1 through C2
- `docs/WORLD_TAXONOMY_V1.md` — canonical Practice worlds
- `docs/LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md` — how `english-course` language becomes deliberately authored Practice conversation
- `docs/MISSION_CONTRACT_V1.md` — full mission schema: grounding, canonical dialogue, semantic graph, hints and preview
- `docs/DYNAMIC_HINTS_V1.md` — live contextual hint behaviour
- `docs/LISTENING_PREVIEW_V1.md` — optional pre-mission example conversation variant
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

## Mission authoring structure

```text
Real communicative goal
  -> language grounding from english-course
  -> canonical dialogue written by Englotti
  -> semantic graph / branches
  -> Listening Preview variant
  -> bounded Gemini Live performance
  -> adversarial audio QA
```

Core principle:

> **We write the conversation. Gemini performs and adapts it.**

For contextual support:

> **We author the intent. Gemini authors the help.**

Those two rules work together: Gemini may adapt and support a real conversation, but it does not own the pedagogical structure or normal-path language design.

## Current curriculum work

A1 now has a first full map of **24 candidate missions across the 7 worlds**, with **8 Core / Great place to start missions**.

Core is recommendation, not prerequisite.

Before bulk-writing detailed mission contracts, the current plan is to finish the visible A1–C2 map and review cross-level progression. Then Core missions are promoted one by one through the grounded-dialogue authoring factory.

`Order a drink` is the first mission already upgraded to this model: its A1 ability/grammar/phrase/word grounding, canonical conversation, semantic beats, dynamic hints and Listening Preview variant are all stored together in the mission source.

Do not bulk-author mission files just to hit a lesson count.
