# Authored Mission Contract v1

A Practice mission is a reviewed conversational experience.

It contains **both**:

1. a reviewed canonical conversation written by Englotti, and
2. a semantic graph that lets Gemini perform/adapt that conversation naturally without becoming the curriculum writer.

The mission owns the level, selected language grounding, roles, scenario truth, canonical dialogue, conversation beats, learner intents, branches and correction boundaries.

> **We write the conversation. Gemini performs and adapts it.**

The canonical conversation is not a password script the learner must reproduce.

## Canonical shape

```yaml
id: practice.a1.food.order-drink.v1
revision: 2
status: pilot
level: A1
world: food-shopping
library_role: core
title: Order a drink
estimated_minutes: 4

learner_role: customer
ai_role: cafe cashier
setting: small cafe
mission_goal: Order one drink, answer one predictable service question, complete the payment exchange, and close naturally.

language_grounding:
  source_repo: addvaluewithai-hub/english-course
  source_level: A1
  inventory_scope: cumulative_through_level
  abilities:
    - id: ability.cefr_all_descriptors.cefr.cv2020.p078.a1.obtaining_goods_and_services.002
      role: core_communicative_grounding
    - id: ability.cefr_all_descriptors.cefr.cv2020.p078.a1.obtaining_goods_and_services.003
      role: cost_quantity_grounding
  grammar:
    - id: egp.1741163710391x459074403345042000
      label: can for requests
      role: productive_opportunity
    - id: egp.1741163711300x569087712695511000
      label: would like for wishes/preferences
      role: productive_opportunity
  phrases:
    - id: oxford.phrase.online.0076
      phrase: ask for sth
    - id: oxford.phrase.online.0668
      phrase: Thank you
  words:
    - id: oxford.o3000.p01.154
      word: coffee
    - id: oxford.o3000.p03.237
      word: tea
    - id: oxford.o3000.p04.054
      word: water
  authoring_note: Selected language opportunities and boundaries, not mandatory learner checks.

truth:
  menu_items: [coffee, tea, water]
  sizes: [small, large]

canonical_dialogue:
  purpose: reference_path_not_required_script
  turns:
    - beat: greet_order
      speaker: ai_role
      text: Hello. What would you like?
    - beat: greet_order
      speaker: learner
      text: Can I have a coffee, please?
    - beat: choose_size
      speaker: ai_role
      text: Small or large?
    - beat: choose_size
      speaker: learner
      text: Small, please.
    - beat: price
      speaker: ai_role
      text: Three dollars, please.
    - beat: price
      speaker: learner
      text: Okay. Thank you.
    - beat: close
      speaker: ai_role
      text: Thank you.

runtime:
  surface_freedom: tight
  default_hint_mode: tap

beats:
  - id: greet_order
    type: required
    ai_intent: Greet the learner and ask what they would like.
    preferred_realizations:
      - Hello. What would you like?
      - Hi. What can I get for you?
    learner_intent: Request one available drink politely.
    overview_ar: اطلب المشروب اللي عايزه
    correction_focus:
      - correct a genuine request-form error when it matters
      - accept natural alternative wording
    next: choose_size

  - id: choose_size
    type: required
    ai_intent: Ask whether the learner wants small or large.
    preferred_realizations:
      - Small or large?
    learner_intent: Choose one offered size.
    overview_ar: اختار الحجم
    next: price

  - id: price
    type: required
    ai_intent: State the correct price and allow the learner to complete the exchange.
    preferred_realizations:
      - Three dollars, please.
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

listening_preview:
  status: authored
  purpose: orientation_not_rehearsal
  relationship_to_canonical: same_shape_reviewed_variant
  transcript_default: hidden
  transcript:
    - speaker: ai_role
      text: Hi. What would you like?
    - speaker: customer
      text: I'd like a tea, please.
    - speaker: ai_role
      text: Small or large?
    - speaker: customer
      text: Large, please.
  audio_asset: null
```

## Required mission fields

Every published authored mission must define:

- stable ID and revision
- CEFR level
- world/context
- `library_role`: `core` or `library`
- learner role
- AI role
- concrete mission goal
- selected language grounding from the reviewed Englotti level source of truth
- stable scenario truth / facts
- reviewed canonical dialogue from opening to natural ending
- required conversation beats
- preferred AI realizations where useful, especially at lower levels
- optional branches where genuinely useful
- learner intent for each meaningful move
- accepted semantic alternatives/boundaries where needed
- correction focus / language boundaries
- exit / success conditions
- runtime surface freedom appropriate to the level
- contextual hint policy
- Listening Preview metadata where included or required by level policy

Optional `overview_ar` is learner-facing mission preview copy. It is **not** the runtime hint.

`library_role: core` means **Great place to start**. It does not create a prerequisite or mandatory order.

## Language grounding

Practice uses `addvaluewithai-hub/english-course` as the shared language source of truth.

Grounding may reference:

- communicative abilities
- grammar
- phrases
- words
- pronunciation/performance constraints when relevant

The inventory is used to **write and constrain the conversation**.

It is not a requirement that the learner produce every referenced item.

A mission should record items that materially informed:

- canonical dialogue language
- live surface bounds
- correction focus
- Listening Preview wording
- contextual hint support

Do not tag every function word mechanically.

Level inventory semantics are cumulative for Practice authoring: an A2 mission may use reviewed A1 + A2 language; B1 may use reviewed language through B1, and so on.

See `LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md`.

## Canonical dialogue

A full mission is not complete with only intents and a prompt.

The `canonical_dialogue` is a reviewed end-to-end reference conversation written by Englotti.

It establishes:

- what level-safe natural language sounds like in this mission
- expected AI and learner turn length
- interaction rhythm
- useful phrase/grammar opportunities
- a stable reference for Listening Preview variants
- a stable baseline for Live QA

The canonical dialogue is **not** what the learner is required to say.

For A1, Gemini should normally stay close to the authored AI language on the normal path. Higher levels allow progressively more surface freedom.

## Canonical dialogue versus semantic graph

The canonical dialogue answers:

> What is one high-quality version of this conversation?

The semantic graph answers:

> What is each turn doing, what counts as success, what alternatives/branches are allowed, and how should the live conversation recover when it differs from the reference path?

Example canonical learner line:

```text
Can I have a coffee, please?
```

Semantic learner intent:

```text
request one available drink politely
```

Depending on level/context, valid alternatives may include:

```text
Coffee, please.
I'd like a tea, please.
Could I get some water, please?
```

The runtime judges meaning and naturalness, not string similarity.

## Preferred realizations

A beat may contain reviewed `preferred_realizations` for Gemini's line.

These are especially valuable at A1/A2 because they keep the live partner near language we deliberately wrote and level-checked.

They are anchors, not exact-string constraints.

If the learner creates a valid detour, Gemini may use new language required to respond naturally, while remaining inside level/truth bounds as much as possible.

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

is a valid alternative and should not be corrected merely because it differs from the canonical line.

After a genuine current-beat error, give a short natural correction and let the learner retry before advancing when the corrected form matters to the task.

## Contextual hint bundle

Runtime hints are **not hardcoded answer cards**.

When the learner taps Hint, the existing live agent uses:

- actual conversation so far
- current beat/learner intent
- scenario truth
- mission level
- selected language grounding
- canonical/preferred language as support anchors

to generate a complete structured support bundle in **one tool call**:

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

## Listening Preview

A mission may include an optional authored Listening Preview.

The preview is:

- one plausible version of the same situation
- written from the same language grounding as the canonical dialogue
- normally a reviewed variant, not a duplicate script
- fixed/reviewed content for the mission revision
- orientation, not rehearsal
- skippable by the learner
- separate from speaking evidence

The live mission is **not bound to the preview transcript**.

For A1 Core missions, an authored preview transcript + audio asset is required before full publication. During contract drafting, `audio_asset: null` is acceptable.

See `LISTENING_PREVIEW_V1.md`.

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

For branching missions, author at least one canonical/main path and reviewed branch exemplars where they materially control language or pragmatics.

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

- `tight` — A1-heavy; stay close to canonical/preferred realizations on normal path, short turns, mostly linear flow
- `bounded` — A2/B1; natural paraphrase plus authored branches
- `open_within_graph` — B2+; greater wording/discourse freedom while preserving graph/truth/goal/pragmatic constraints

This is not a learner-facing difficulty switch.

## Mission completion

Completion means the learner handled the mission sufficiently to reach a valid ending. It does not automatically mean mastery of every grounded language item used in the conversation.

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

Listening Preview playback is not included as speaking independence evidence.

## Authoring anti-patterns

Do not publish missions that:

- are only a role prompt with no authored conversation
- contain only a semantic graph and leave normal-path wording entirely to Gemini
- require exact memorized responses from the canonical dialogue
- force every grounded vocabulary/grammar item into learner production
- treat grounded language as a hidden pass/fail checklist
- hardcode the primary runtime hint ladder as if the conversation cannot move
- use the Listening Preview as the script the learner must reproduce
- make Listening Preview mandatory to unlock the mission
- hide the learner's goal and accidentally test memory of turn order
- force a large vocabulary checklist into one interaction
- create fake misunderstandings only to trigger repair
- make the AI carry the entire conversation
- use hint content that reveals personal data
- hardcode learner names, ages, cities, jobs, phone numbers, or other personal details
- equate one successful mission with level mastery
