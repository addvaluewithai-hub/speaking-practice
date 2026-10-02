# Practice Architecture v2

Status: **current**

Supersedes `PRACTICE_ARCHITECTURE_V1.md` where the two differ.

## 1. Product definition

Practice is a **level-aware library of authored real-life conversations, performed dynamically by Gemini Live**.

It is not:

- a second linear English course
- a random scenario browser
- a fixed dialogue player
- a free chat with a level label

## 2. Product modes

### Authored Practice

Reviewed mission with:

- known CEFR level
- authored real-world goal
- authored semantic conversation graph
- stable scenario truth
- bounded runtime freedom
- dynamic contextual hints
- reviewed correction boundaries
- optional Listening Preview
- QA-backed completion conditions

### Custom Practice

Learner requests a situation. Runtime may generate a temporary mission/blueprint. Calibration and QA confidence are lower than authored Practice.

### Free Speak

Open conversation without an authored mission graph.

## 3. Learner navigation

Primary path:

```text
Practice
  -> level
  -> world
  -> mission
  -> optional Listening Preview
  -> live conversation
  -> recap / retry
```

Levels:

```text
A1 A2 B1 B2 C1 C2
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

The learner's current level is the default filter, not a lock.

There is no `Lesson 17 of 45` requirement.

## 4. Practice Map versus mission contracts

`PRACTICE_MAP_V1.md` is the library design map:

- level
- world
- mission title
- real communicative goal
- interaction shape
- Core/library status

`missions/` contains detailed reviewed implementations of individual missions.

This separation prevents us from authoring dozens of detailed contracts before seeing gaps and repetition across a level.

## 5. Core missions

A level may mark a small number of missions as:

> Great place to start

Core means recommended orientation, not prerequisite and not a hidden sequence.

Learners may enter any available mission at their level.

## 6. Difficulty model

Difficulty belongs to the authored mission contract.

Do not use one scenario with a learner-facing Easy/Medium/Hard switch.

The communication problem itself changes across levels.

Example:

```text
A1: order a drink
A2: order with preferences
B1: resolve a wrong order
B2: negotiate an alternative under constraints
C1: manage a sensitive complaint with tact
C2: mediate a complex dispute with layered implications
```

Hints change support, not mission level.

## 7. Conversation blueprint

A mission is an authored **semantic graph**, not a fixed script.

We author:

- mission goal
- roles
- scenario truth
- AI intent per beat
- learner intent per beat
- required/optional branches
- correction focus
- recovery boundaries
- natural ending condition

Gemini controls natural surface wording inside those boundaries.

Lower levels use tighter, more predictable graphs. Higher levels permit more branching and discourse freedom.

## 8. Dynamic hint architecture

Runtime hints are generated from the actual live conversation.

Core rule:

> **We author the intent. Gemini authors the help.**

On the first Hint request in an active beat, Gemini returns one complete private UI bundle:

```text
Arabic communicative intent
optional Arabic context/recovery note
useful English words/chunks
one full natural English response example
```

The UI caches the complete bundle and reveals it progressively.

There are no extra model requests for deeper support in the same active beat.

Changing beats invalidates the bundle.

A hint request never advances the mission and never counts as learner speech.

See `DYNAMIC_HINTS_V1.md`.

## 9. Listening Preview

An authored mission may include an optional Listening Preview:

> one plausible version of this situation

It is orientation, not rehearsal and not a script to reproduce.

Rules:

- learner can always skip it
- transcript/audio are authored/reviewed and fixed for the mission revision
- the live mission may use different wording and concrete choices
- listening creates no independent speaking evidence
- A1 Core missions require a preview asset before full publication
- higher levels use previews selectively

See `LISTENING_PREVIEW_V1.md`.

## 10. Correction policy

Different valid English is valid.

Runtime behaviour:

- valid natural alternative -> accept and continue
- genuine important current-target error -> brief correction, usable natural form, retry when needed
- minor non-target issue with clear meaning -> usually continue
- unclear meaning -> clarify

Do not make Practice grammar-police conversation.

## 11. Branching and detours

The graph is a guardrail, not a railroad.

A learner may:

- ask a reasonable unexpected question
- choose a valid alternative
- change their mind
- take an authored branch
- briefly detour

Gemini should react naturally while preserving scenario truth and returning toward the mission goal when needed.

## 12. Progress model

Useful signals:

- missions completed
- worlds practised
- hint levels used
- full help reveals
- corrections/retries
- branch paths
- successful replay with less support

Completion is evidence from one situation, not broad mastery.

Avoid false-precision grammar/vocabulary percentages from one conversation.

## 13. Sources

Mission authoring hierarchy:

```text
real communicative goal
-> CEFR interaction difficulty
-> Englotti shared-English level boundary
-> real-world workflow/truth
-> authored mission graph
-> Gemini Live/audio QA
```

Practice does not mirror Learn lesson order.

See `SOURCES.md`.

## 14. Current production strategy

1. Map the level before bulk-authoring contracts.
2. Review coverage and overlap.
3. Promote a small set of Core missions to full contracts.
4. Add required Listening Previews.
5. Run adversarial Live QA.
6. Expand the level only after the mission factory remains reliable.
7. Map the next level so cross-level progression stays visible.

The current map starts with A1 in `PRACTICE_MAP_V1.md`.
