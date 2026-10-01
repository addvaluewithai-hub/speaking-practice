# Practice Architecture v1

## 1. Definition

Practice is a **level-aware mission library**, not a second curriculum.

A learner should be able to open Practice and immediately see missions appropriate to their current CEFR level. They may browse other levels, but level is the default filter so learners do not need trial-and-error to discover what is suitable.

## 2. Product modes

### Authored Practice
Reviewed mission, known level, authored conversation blueprint, authored hints, bounded branching, predictable QA surface.

### Custom Practice
Learner requests a situation. Runtime may generate a temporary blueprint, but calibration and evidence claims are weaker than authored Practice.

### Free Speak
Open conversation. No authored mission blueprint and no assumption that a specific communicative goal will occur.

## 3. Navigation model

Primary dimensions:

- **Level:** A1, A2, B1, B2, C1, C2
- **World / context:** People & Social, Food & Shopping, Travel & Transport, Home & Services, Work & Study, Plans & Leisure, plus future reviewed worlds

Optional metadata can include goal, duration, interaction shape, and recommendation tags.

There is no required `Practice lesson 17 of 45` sequence.

## 4. Difficulty model

Difficulty belongs to the mission contract.

The same real-world context can appear at several levels as separately authored missions:

- A1 cafe: order one drink and close
- A2 cafe: order with simple preferences or a small change
- B1 cafe: resolve a wrong order or timing problem
- B2 cafe: negotiate an alternative under constraints
- C1+: manage nuance, tact, implication, or complex trade-offs where appropriate

Hints never change the mission level. They change only the amount of support.

## 5. Conversation blueprint

A mission is not a rigid transcript and not an unconstrained prompt.

It is an authored graph of semantic conversation beats:

```text
mission goal
  -> beat / intent
      -> expected learner intent
      -> hint ladder
      -> accepted semantic alternatives
      -> optional branches
      -> recovery rules
  -> exit condition
```

Gemini Live acts inside the current beat. It may phrase its line naturally as long as it preserves the authored function, information, level, and branch state.

Lower levels may use tighter wording and more linear graphs. Higher levels may allow wider surface variation and more branching.

## 6. Hint system

Learner preference:

- `Auto`
- `Tap to show`
- `Off`

Support ladder for an authored learner move:

1. **Intent hint** — usually a short Arabic cue describing what to communicate
2. **Useful words** — limited English words/chunks, not a full answer
3. **Full help** — one usable complete response

Example:

```text
AI: Sorry, there are no tables inside right now.

Intent hint:
اسأل لو فيه مكان بره

Useful words:
outside · table · available

Full help:
Do you have a table outside?
```

A full answer reveal is supported practice, not independent production.

## 7. Correction policy

The runtime distinguishes **error** from **valid variation**.

If the learner expresses the intended meaning naturally with a different valid sentence, continue without correction.

If the learner makes a genuine important error in the current mission target, Otti gives a brief usable correction and continues.

Example:

```text
Learner: Where she live?
Otti: Almost — say, "Where does she live?" She lives in Cairo.
```

Do not turn the mission into a grammar lecture unless the learner explicitly asks for explanation.

## 8. Branching and recovery

Blueprints are not railroads.

If the learner makes a sensible move different from the most likely authored path, Gemini may enter an allowed branch or recover toward the mission goal.

The mission contract defines:

- required beats
- optional beats
- branch triggers
- information that must stay consistent
- forbidden shortcuts / answer leakage
- natural ending conditions

## 9. Progress and observations

Practice can show useful progress without pretending to be a linear syllabus.

Useful learner-facing signals include:

- missions completed
- worlds practised
- turns completed independently
- intent hints used
- useful-word hints used
- full responses revealed
- successful retries with less support

Do not present false-precision grammar/vocabulary percentages from one conversation.

One completed mission is evidence from one context, not broad mastery.

## 10. Recommendation model

Future recommendations may combine:

```text
learner level
+ recent mission history
+ worlds under-practised
+ support dependence
+ observed communication needs
+ freshness / replay history
-> suggested missions
```

Recommendations should never turn Practice into a hidden mandatory sequence.

## 11. Separation from Learn

Learn and Practice may share level knowledge and learner profile information, but Practice is designed from its own real-life mission goals.

Practice is not required to mirror Learn lessons, cover every Learn item, or wait for Learn completion.

Learn answers: **How do I learn this English?**

Practice answers: **Can I use English to handle this situation?**
