# Practice Architecture v2

Status: **current source of truth**

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
- language grounding from the reviewed Englotti level inventory
- authored canonical conversation path
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

## 7. Language grounding and authored conversation

Authored Practice does **not** start with a free-form Gemini scenario prompt.

Full mission authoring follows:

```text
real communicative goal
-> language grounding
-> canonical authored dialogue
-> semantic graph
-> Listening Preview variant
-> Gemini Live bounds
-> Live QA
```

The shared `addvaluewithai-hub/english-course` inventories provide reviewed words, phrases, grammar, abilities and level expectations. Practice deliberately selects from that language to write conversations appropriate to the mission and level.

The inventories are authoring material and level control, **not a hidden checklist the learner must reproduce**.

Core rule:

> **We write the conversation. Gemini performs and adapts it.**

Every full mission should contain a `canonical_dialogue`: one reviewed, complete, plausible version of the interaction from opening to ending.

The canonical dialogue controls:

- level-safe language
- expected turn length/density
- tone and interaction shape
- preferred surface realizations
- a stable basis for Listening Preview authoring and runtime QA

It is a reference path, not a learner password script.

See `LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md`.

## 8. Conversation blueprint

A mission contains both an authored dialogue **and** an authored semantic graph.

The graph explains what the dialogue is doing and how the live conversation may adapt.

We author:

- mission goal
- roles
- scenario truth
- canonical dialogue
- AI intent per beat
- preferred AI realizations where useful
- learner intent per beat
- required/optional branches
- accepted semantic alternatives
- correction focus
- recovery boundaries
- natural ending condition

Gemini may vary surface wording while preserving the authored function, level, truth and graph.

Lower levels use tighter freedom and stay much closer to reviewed wording. Higher levels permit more branching and discourse freedom.

The graph is therefore a guardrail around an authored conversation, not a substitute for writing one.

## 9. Dynamic hint architecture

Runtime hints are generated from the actual live conversation.

Core rule:

> **We author the intent. Gemini authors the contextual help.**

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

The hint generator should receive the mission's level grounding and authored language anchors so its help remains level-safe, but it must adapt to the conversation that actually happened.

See `DYNAMIC_HINTS_V1.md`.

## 10. Listening Preview

An authored mission may include an optional Listening Preview:

> one plausible version of this situation

It is orientation, not rehearsal and not a script to reproduce.

The preview is written from the **same language grounding and interaction shape** as the canonical dialogue, normally as a reviewed variant using different concrete choices and/or valid wording.

Rules:

- learner can always skip it
- transcript/audio are authored/reviewed and fixed for the mission revision
- the live mission may use different wording and concrete choices
- listening creates no independent speaking evidence
- A1 Core missions require a preview asset before full publication
- higher levels use previews selectively

See `LISTENING_PREVIEW_V1.md`.

## 11. Live surface freedom

Gemini is an actor/adaptive partner, not the curriculum writer.

Typical freedom:

- **A1:** very close to canonical/preferred language; short predictable turns; deviation mainly for valid detours, clarification, correction or scenario truth
- **A2:** close but more flexible; bounded natural paraphrase and follow-ups
- **B1:** canonical path plus authored branches; wider natural realization
- **B2–C2:** wider discourse freedom inside tightly authored goals, truth, pragmatic constraints and branch structure

A valid learner alternative may move the live wording away from the reference dialogue. That is expected.

## 12. Correction policy

Different valid English is valid.

Runtime behaviour:

- valid natural alternative -> accept and continue
- genuine important current-target error -> brief correction, usable natural form, retry when needed
- minor non-target issue with clear meaning -> usually continue
- unclear meaning -> clarify

The canonical dialogue and language grounding may guide useful correction, but Gemini must not force the learner to reproduce the canonical sentence merely because it was authored.

Do not make Practice grammar-police conversation.

## 13. Branching and detours

The graph is a guardrail, not a railroad.

A learner may:

- ask a reasonable unexpected question
- choose a valid alternative
- change their mind
- take an authored branch
- briefly detour

Gemini should react naturally while preserving scenario truth and returning toward the mission goal when needed.

## 14. Progress model

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

## 15. Sources

Mission authoring hierarchy:

```text
real communicative goal
-> CEFR interaction difficulty
-> Englotti shared-English level inventory
-> selected language grounding
-> real-world workflow/truth
-> canonical authored dialogue
-> semantic graph + runtime bounds
-> Listening Preview variant
-> Gemini Live/audio QA
```

Practice does not mirror Learn lesson order.

See `SOURCES.md` and `LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md`.

## 16. Current production strategy

1. Map A1-C2 before bulk-authoring detailed contracts.
2. Review cross-level coverage and communication-problem progression.
3. Promote a small set of Core missions to full contracts.
4. Ground each promoted mission in the reviewed level inventory.
5. Write the canonical dialogue before finalizing the semantic graph.
6. Write the Listening Preview as a reviewed variant where required/useful.
7. Compile canonical language + graph + truth into bounded Gemini Live instructions.
8. Run adversarial Live QA.
9. Expand only after the mission factory remains reliable.

The current map starts with A1 in `PRACTICE_MAP_V1.md`.
