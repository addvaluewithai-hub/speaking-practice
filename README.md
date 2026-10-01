# Englotti Speaking Practice

A clean source of truth for designing **Practice** in Englotti.

Practice is not a second English course and not a random scenario browser.

> **Practice = a level-aware library of authored real-life conversations, performed dynamically by Gemini Live.**

## Product boundary

- **Learn** teaches English through a guided curriculum.
- **Practice** lets learners use English in authored, level-controlled real-life missions.
- **Custom Practice** lets a learner request a scenario that is generated at runtime.
- **Free Speak** is open conversation without an authored mission blueprint.

Practice has **no linear lesson sequence** such as `Lesson 1 -> Lesson 2 -> Lesson 3`.

Instead, learners enter at their current level (`A1` to `C2`) and browse/replay missions by world or goal. The default view should show missions appropriate to the learner's level; other levels remain explorable rather than locked.

## Core design principles

1. **Mission difficulty is authored.** A1 and B2 versions of a hotel situation are separate missions, not one scenario with an Easy/Hard switch.
2. **Conversation is designed by us.** Gemini performs and adapts inside an authored conversation blueprint; it does not invent the pedagogical structure.
3. **Blueprints are semantic, not rigid transcripts.** We author conversation beats, learner intents, branches, and exit conditions. Gemini may phrase its own turn naturally inside those bounds.
4. **Hints are support, not difficulty.** A learner may use `Auto`, `Tap to show`, or `Off` support without changing the mission's CEFR level.
5. **Different valid English is valid.** The learner is never required to reproduce one memorized sentence when another natural form achieves the same intent.
6. **Correct genuine errors, not variation.** Otti briefly corrects a real target-language error, gives the usable form, then continues the conversation.
7. **Authored help is measurable.** We distinguish no help, intent hint, useful-word hint, and full response reveal.
8. **Mission completion is not mastery.** Practice can record useful observations without pretending one conversation proves a broad ability.
9. **Custom and Free Speak are separate runtime modes.** They do not inherit the quality guarantees of authored missions.

## Repository map

- `docs/PRACTICE_ARCHITECTURE_V1.md` — product and runtime architecture
- `docs/LEVEL_BIBLE_V1.md` — what changes from A1 through C2
- `docs/MISSION_CONTRACT_V1.md` — canonical authored mission schema
- `docs/SOURCES.md` — external and internal grounding sources
- `missions/` — reviewed authored conversation missions and blueprints

## First build target

Do not bulk-author A1-C2 yet.

First prove the mission factory with a small vertical slice:

- 6 authored A1 missions across different worlds
- 3 authored B1 missions with meaningful branches and complications
- real Gemini Live QA for alternative valid language, genuine errors, hesitation, hints, interruptions, clarification, off-path but valid learner moves, and natural endings

Only after that architecture survives real conversations should the library scale.
