# Dynamic Practice Hints v1

Practice hints are **generated from the live conversation context**, not rendered from fixed authored sentences.

The authored mission owns:

- level
- language grounding
- canonical dialogue / learner models
- scenario truth
- current learner intent
- graph
- correction boundaries

Gemini owns the wording of the help for the conversation that actually happened.

## Core rule

> We author the intent. Gemini authors the help.

A hint request must never turn Gemini into the mission designer. The model generates support only inside the current authored beat and mission constraints.

The mission's canonical/grounded language should act as a **support anchor**, not as a password answer.

## One model request per active beat

When the learner taps **Hint** for the first time in the current beat, the app sends one private UI control event to the existing Gemini Live session.

Each request gets a short-lived `request_id`. Gemini must echo that ID in the tool call so a late response from an older request cannot populate a newer hint.

Gemini must answer that event by calling a structured client tool once with the **complete hint bundle**:

```json
{
  "request_id": "f8f0...",
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

Gemini should use all of the following:

- whole conversation so far
- current semantic beat / learner intent
- scenario truth
- CEFR level
- mission language grounding
- canonical learner models / reference dialogue as examples of level-safe language

Example: the authored learner intent is `request one available drink politely`.

If the conversation is still on the expected path:

```text
Cashier: What would you like?
```

A suitable intent hint could be:

```text
اطلب المشروب اللي عايزه
```

And the useful language may naturally reuse authored A1 anchors such as:

```text
Can I have ...?
I'd like ...
please
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

### `request_id`

Exact correlation ID from the active UI hint request. The runtime rejects missing, stale or mismatched IDs.

### `intent_ar`

A short Egyptian-Arabic description of the learner's best next communicative move now. It should express meaning, not translate a password sentence.

### `context_ar`

Optional. A short contextual/recovery note when what just happened matters to the hint. Leave empty when unnecessary.

### `useful_language_en`

Two to five short English words or chunks appropriate to the current level and current moment.

Prefer mission-grounded / reviewed language when it fits the actual conversation.

Do not force a grounded item when a different simpler expression is more useful in context.

### `full_response_en`

One natural complete learner response that would work **now**.

The canonical learner line may be used when it fits the current context, or Gemini may generate another level-safe valid response. Either way it remains a support example, never the only accepted answer.

## Safety and pedagogy rules

- A UI hint request is not learner speech and not evidence of an answer attempt.
- Requesting or revealing a hint never advances the authored beat; the runtime freezes beat advancement while the request is active.
- A valid learner alternative remains valid even when it differs from `full_response_en` or the canonical dialogue.
- Full-response help counts as stronger support than an intent hint.
- Keep generated support inside the mission's CEFR level, language grounding and scenario truth.
- Never insert learner personal details into a generated hint.
- Gemini must not call the hint tool proactively; a live UI request must be active.
- The runtime rejects stale payloads whose `request_id` or `beat_id` no longer matches the active request.
- If generation fails or times out, let the learner retry the hint request; do not silently substitute a fixed answer card as the normal path.
- Reopening an already cached hint does not count as a new hint-use event; telemetry records the highest support layer revealed per beat.

## Authoring implication

Mission files should not contain the exact user-facing hint ladder as the primary experience.

They should contain:

- language grounding
- canonical dialogue / reviewed learner models
- `learner_intent`
- scenario truth
- CEFR/runtime bounds
- correction focus
- optional learner-facing mission overview text
- the dynamic hint policy

The canonical dialogue gives Gemini controlled level-safe language anchors. The semantic graph controls meaning. The help wording remains contextual at runtime.
