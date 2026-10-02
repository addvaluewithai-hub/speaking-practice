# Dynamic Practice Hints v1

Practice hints are **generated from the live conversation context**, not rendered from fixed authored sentences.

The authored mission still owns the level, scenario truth, current learner intent, graph and correction boundaries. Gemini owns the wording of the help for the conversation that actually happened.

## Core rule

> We author the intent. Gemini authors the help.

A hint request must never turn Gemini into the mission designer. The model generates support only inside the current authored beat and mission constraints.

## One model request per active beat

When the learner taps **Hint** for the first time in the current beat, the app sends one private UI control event to the existing Gemini Live session.

Gemini must answer that event by calling a structured client tool once with the **complete hint bundle**:

```json
{
  "beat_id": "greet_order",
  "intent_ar": "اختار مشروب من الموجود واطلبه",
  "context_ar": "هو قال إن المتاح قهوة أو شاي أو مية.",
  "useful_language_en": ["I'd like ...", "Can I have ...?", "please"],
  "full_response_en": "Can I have a tea, please?"
}
```

The tool payload is private UI data. Otti must not read it aloud or add a spoken explanation after the tool call.

The UI caches this bundle for the active beat and reveals it progressively:

1. Arabic intent (+ context note when useful)
2. useful English words/chunks
3. one full natural example

Levels 2 and 3 are revealed from the cached bundle. They **must not create additional Gemini requests**.

If the learner hides the hint and opens it again in the same beat, reuse the same cached bundle.

When the authored beat changes, invalidate the old bundle. The first hint request in the new beat may generate a new bundle.

## Context-sensitive generation

Gemini should use the whole conversation so far.

Example: the authored learner intent is `request one available drink politely`.

If the conversation is still on the expected path:

```text
Cashier: What would you like?
```

A suitable intent hint could be:

```text
اطلب المشروب اللي عايزه
```

But after a detour:

```text
Learner: What do you have?
Cashier: We have coffee, tea and water.
```

The hint should adapt:

```text
اختار واحد من المشروبات اللي قالهالك واطلبه
```

And after an unavailable option:

```text
Learner: Do you have orange juice?
Cashier: Sorry, we don't. We have coffee, tea and water.
```

The hint should help recovery:

```text
اختار بديل من الموجود واطلبه
```

It should not fall back to a generic prewritten card when the live context gives better information.

## Bundle fields

### `intent_ar`

A short Egyptian-Arabic description of the learner's best next communicative move now. It should express meaning, not translate a password sentence.

### `context_ar`

Optional. A short contextual/recovery note when what just happened matters to the hint. Leave empty when unnecessary.

### `useful_language_en`

Two to five short English words or chunks appropriate to the current level and current moment.

### `full_response_en`

One natural complete learner response that would work **now**. It is a support example, never the only accepted answer.

## Safety and pedagogy rules

- A UI hint request is not learner speech and not evidence of an answer attempt.
- Requesting or revealing a hint never advances the authored beat.
- A valid learner alternative remains valid even when it differs from `full_response_en`.
- Full-response help counts as stronger support than an intent hint.
- Keep generated support inside the mission's CEFR level and scenario truth.
- Never insert learner personal details into a generated hint.
- Gemini must not call the hint tool proactively; a live UI request must be active.
- The runtime should reject stale hint payloads whose `beat_id` no longer matches the current beat.
- If generation fails or times out, let the learner retry the hint request; do not silently substitute a fixed answer card as the normal path.

## Authoring implication

Mission files should not contain the exact user-facing hint ladder as the primary experience.

They should contain:

- `learner_intent`
- scenario truth
- CEFR/runtime bounds
- correction focus
- optional learner-facing mission overview text
- the dynamic hint policy

The conversation graph remains authored. The support wording is contextual at runtime.
