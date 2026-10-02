# Authored Mission Contract v1

A Practice mission is a reviewed conversational experience. It is authored as a **semantic graph**, not a fixed dialogue transcript.

The mission owns the level, roles, scenario truth, conversation beats, learner intents, branches and correction boundaries. Gemini performs the role naturally inside those boundaries.

## Canonical shape

```yaml
id: practice.a1.food.order-drink.v1
revision: 1
status: pilot
level: A1
world: food-shopping
title: Order a drink
estimated_minutes: 4

learner_role: customer
ai_role: cafe cashier
setting: small cafe
mission_goal: Order one drink, answer one predictable service question, complete the payment exchange, and close naturally.

truth:
  menu_items: [coffee, tea, water]
  sizes: [small, large]

runtime:
  ai_freedom: tight
  default_hint_mode: tap

beats:
  - id: greet_order
    type: required
    ai_intent: Greet the learner and ask what they would like.
    learner_intent: Request one available drink politely.
    overview_ar: اطلب المشروب اللي عايزه
    correction_focus:
      - correct a genuine request-form error when it matters
      - accept natural alternative wording
    next: choose_size

  - id: choose_size
    type: required
    ai_intent: Ask whether the learner wants small or large.
    learner_intent: Choose one offered size.
    overview_ar: اختار الحجم
    next: price

  - id: price
    type: required
    ai_intent: State the correct price and allow the learner to complete the exchange.
    learner_intent: Acknowledge and complete payment politely.
    overview_ar: كمّل الدفع واقفل الطلب
    next: close

  - id: close
    type: ending
    ai_intent: Close the transaction naturally and briefly.
    learner_intent: Optional polite closing.

hint_policy:
  generation: live_contextual_bundle
  trigger: learner_taps_hint
  request_count: one_model_request_per_active_beat
  cache_scope: active_beat
```

## Required mission fields

Every published authored mission must define:

- stable ID and revision
- CEFR level
- world/context
- learner role
- AI role
- concrete mission goal
- stable scenario truth / facts
- required conversation beats
- optional branches where genuinely useful
- learner intent for each meaningful move
- correction focus / language boundaries
- exit / success conditions
- runtime freedom appropriate to the level
- contextual hint policy

Optional `overview_ar` is learner-facing mission preview copy. It is **not** the runtime hint.

## Semantic beats, not passwords

The mission defines what the learner is trying to accomplish, not one required sentence.

If the learner intent is:

```text
ask whether an outside table is available
```

all of these may be acceptable depending on level/context:

```text
Do you have a table outside?
Is there anywhere to sit outside?
Can we sit outside?
```

The runtime judges meaning and naturalness, not string similarity.

## Error versus variation

The mission contract should define **what matters**, not enumerate every correct sentence.

Example:

```text
Where she live?
```

is a genuine current-target error and may receive a concise correction:

```text
Almost — say, "Where does she live?"
```

But:

```text
What city does she live in?
```

is a valid alternative and should not be corrected merely because it differs from a common model sentence.

After a genuine current-beat error, give a short natural correction and let the learner retry before advancing when the corrected form matters to the task.

## Contextual hint bundle

Runtime hints are **not hardcoded answer cards**.

When the learner taps Hint, the existing live agent uses the conversation context, current beat, scenario truth and level to generate a complete structured support bundle in **one tool call**:

```json
{
  "beat_id": "greet_order",
  "intent_ar": "اختار مشروب من الموجود واطلبه",
  "context_ar": "هو قال إن المتاح قهوة أو شاي أو مية.",
  "useful_language_en": ["I'd like ...", "Can I have ...?", "please"],
  "full_response_en": "Can I have a tea, please?"
}
```

The UI caches the complete bundle for the active beat and reveals it progressively:

1. `intent_ar` (+ `context_ar` when useful)
2. `useful_language_en`
3. `full_response_en`

Levels 2 and 3 are UI reveals from the same cached payload. They must not make additional model requests for the same active beat.

Hiding and reopening a hint in the same beat reuses the cache. Changing the active beat invalidates the old bundle.

The full response is a support example, never the only accepted answer.

See `DYNAMIC_HINTS_V1.md` for the runtime contract and QA examples.

## Why hints are generated live

The authored graph controls difficulty, but a real conversation may take a valid detour.

For example, before ordering the learner might ask:

```text
What do you have?
```

or ask for an unavailable item. The next helpful hint should refer to what actually happened rather than show a generic prewritten sentence.

The live agent therefore authors the **help wording**, while the mission continues to author the **learner intent and boundaries**.

> We author the intent. Gemini authors the help.

## Hint safety and bookkeeping

- A hint request is a private UI event, not learner speech.
- Requesting a hint never advances a mission beat.
- The hint tool must not be called proactively.
- The runtime should reject stale tool payloads for an old beat.
- Intent, useful-language and full-response reveals are recorded separately as support telemetry.
- Full-response help is stronger support than an Arabic intent hint.
- Hint text must never inject learner personal details.
- If generation fails, allow another request; do not silently substitute a fixed answer card as the normal path.

## Branching

Use branches only when they represent plausible conversation choices.

Example B1 hotel mission:

```text
report_problem
  -> explain_details
  -> ai_offers_solution
       -> accept -> close
       -> reject -> ask_alternative -> negotiate -> close
```

Do not author branches merely to make a mission look complex.

A1 missions may be mostly linear. Higher levels can allow more authored branch choices and more natural surface variation.

## Scenario truth

Gemini must receive a compact truth object so facts stay consistent.

Examples:

- available menu items and prices
- booking name/date/room type
- opening hours
- train time/platform
- workplace project constraints

The model may phrase facts naturally but must not invent contradictions that invalidate the learner's task.

## Runtime freedom

Suggested values:

- `tight` — A1-heavy; short turns, narrow paraphrase range, mostly linear flow
- `bounded` — A2/B1; natural paraphrase and authored branches
- `open_within_graph` — B2+; greater wording and discourse freedom while preserving graph/truth/goal

This is not a learner-facing difficulty switch.

## Mission completion

Completion means the learner handled the mission sufficiently to reach a valid ending. It does not automatically mean mastery of every language item used in the conversation.

Useful attempt data:

```json
{
  "mission_completed": true,
  "independent_moves": 5,
  "intent_hints": 1,
  "word_hints": 1,
  "full_help_reveals": 0,
  "corrections": 1,
  "branch_path": ["report_problem", "reject", "ask_alternative", "close"]
}
```

## Authoring anti-patterns

Do not publish missions that:

- are only a role prompt with no authored conversation structure
- require exact memorized responses
- hardcode the primary runtime hint ladder as if the conversation cannot move
- hide the learner's goal and accidentally test memory of turn order
- force a large vocabulary checklist into one interaction
- create fake misunderstandings only to trigger repair
- make the AI carry the entire conversation
- use hint content that reveals personal data
- hardcode learner names, ages, cities, jobs, phone numbers, or other personal details
- equate one successful mission with level mastery
