# Authored Mission Contract v1

A Practice mission is a reviewed conversational experience. It is authored as a **semantic graph**, not a fixed dialogue transcript.

## Canonical shape

```yaml
id: practice.a1.food.order-drink.v1
status: draft
level: A1
world: food-shopping
title: Order a drink
estimated_minutes: 3

learner_role: customer
ai_role: cashier
setting: small cafe
mission_goal: Order one drink, respond to one predictable service question, and close naturally.

truth:
  # Stable facts Gemini must not contradict during the mission.
  menu_items: [coffee, tea, water]
  sizes: [small, large]
  prices:
    small: 3
    large: 4

runtime:
  ai_freedom: tight
  max_ai_turn_style: short
  default_hint_mode: tap

beats:
  - id: greet_order
    type: required
    ai_intent: Greet the learner and ask what they would like.
    learner_intent: Order one available drink politely.
    intent_hint_ar: اطلب مشروب
    useful_language:
      - I'd like ...
      - Can I have ...?
      - please
    full_help_examples:
      - I'd like a coffee, please.
      - Can I have a tea, please?
    accepted_semantics:
      - learner clearly requests one available drink
    correction_focus:
      - request form only when the learner's form is genuinely incorrect or unclear
    next: choose_size

  - id: choose_size
    type: required
    ai_intent: Ask whether the learner wants small or large.
    learner_intent: Choose a size.
    intent_hint_ar: اختار الحجم
    useful_language: [small, large]
    full_help_examples:
      - Small, please.
      - A large one, please.
    accepted_semantics:
      - learner clearly selects one offered size
    next: price

  - id: price
    type: required
    ai_intent: State the correct price for the chosen size.
    learner_intent: Acknowledge and complete the exchange.
    intent_hint_ar: وافق وكمل الطلب
    useful_language:
      - okay
      - thanks
      - here you are
    full_help_examples:
      - Okay, thanks.
    next: close

  - id: close
    type: ending
    ai_intent: Close the transaction naturally and briefly.
    learner_intent: Optional polite closing.
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
- optional branches where needed
- learner intent for each meaningful move
- Arabic intent hint where a hint is appropriate
- useful-language support
- full-help examples
- correction focus
- exit / success conditions
- runtime freedom appropriate to the level

## Semantic beats, not passwords

`full_help_examples` are examples, not required answers.

If the intended move is:

```text
اسأل لو فيه مكان بره
```

all of these may be acceptable depending on level/context:

```text
Do you have a table outside?
Is there anywhere to sit outside?
Can we sit outside?
```

The runtime must judge meaning and naturalness, not string similarity.

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

is a valid alternative and should not be corrected merely because it differs from the authored full-help example.

## Hint ladder

Hints are optional runtime support surfaces tied to the current learner intent.

### Level 1 — Intent

Arabic meaning only:

```text
اسأل عن السعر
```

### Level 2 — Useful language

Limited English chunks:

```text
how much · cost · is it
```

### Level 3 — Full help

One or more natural complete examples:

```text
How much is it?
```

The learner may continue after any support level. The attempt records which support was exposed.

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

- `tight` — A1-heavy; short turns, narrow paraphrase range, linear flow
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
- hide the learner's goal and accidentally test memory of turn order
- force a large vocabulary checklist into one interaction
- create fake misunderstandings only to trigger repair
- make the AI carry the entire conversation
- use hint content that reveals personal data
- hardcode learner names, ages, cities, jobs, phone numbers, or other personal details
- equate one successful mission with level mastery
