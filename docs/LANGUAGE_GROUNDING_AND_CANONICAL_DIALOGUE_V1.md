# Language Grounding & Canonical Dialogue v1

Status: **current authoring rule**

Practice missions are not authored from a scenario title plus a free-form Gemini prompt.

For every reviewed mission, Englotti authors a **canonical conversation path** using level-appropriate language grounded in the shared `english-course` source of truth. The semantic graph is then authored around that conversation, and Gemini performs/adapts it live inside explicit bounds.

> **We write the conversation. Gemini performs and adapts it.**

This does **not** mean the learner must repeat a script.

## 1. Authoring pipeline

A full Practice mission is produced in this order:

```text
real communicative goal
  -> language grounding
  -> canonical authored dialogue
  -> semantic conversation graph
  -> Listening Preview variant
  -> Gemini Live bounds
  -> adversarial Live QA
```

The order matters. It prevents the live model from becoming the primary writer of the learner-facing language.

## 2. Role of `english-course`

Primary source:

```text
addvaluewithai-hub/english-course
```

The reviewed level files provide:

- words
- phrases
- grammar
- communicative abilities
- pronunciation/performance boundaries where relevant
- cumulative exit expectations
- source provenance

Level inventories in `english-course` contain items **newly assigned at that level**. Practice authoring should think cumulatively: an A2 mission may use reviewed A1 language plus appropriate A2 language; a B1 mission may use reviewed language through B1, and so on.

Practice does **not** copy Learn lesson order. It uses the shared language inventory as raw material and a level ceiling/floor for writing realistic conversations.

## 3. Language grounding is selective, not a checklist

A mission should deliberately select language that naturally belongs in the real-world interaction.

Example: `A1 / Order a drink` may be grounded in:

- ability: obtain food/drink using basic expressions
- ability: handle simple cost/quantity language
- grammar: `can` for requests
- grammar: `would like` for wishes/preferences
- phrases: `ask for sth`, `Thank you`, `anything else`
- words: `coffee`, `tea`, `water`, `small`, `large`, `dollar`, `please`

This grounding shapes the **authored dialogue** and Gemini's preferred language range.

It does **not** mean:

- every grounded item must appear in every run
- the learner must produce every grounded item
- mission success depends on saying a specific phrase
- Gemini should hunt for vocabulary/grammar evidence instead of having a natural conversation

Use the inventory to write better controlled language, not to create a hidden item checklist.

## 4. Canonical authored dialogue

Every full authored mission should contain at least one reviewed `canonical_dialogue` path.

The canonical dialogue is:

- a complete plausible interaction from opening to natural ending
- written by Englotti, not generated at runtime
- level-safe
- consistent with scenario truth
- intentionally grounded in reviewed level language
- the primary reference for turn length, density, tone and expected interaction shape

Example:

```yaml
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
```

The learner-facing live experience is **not a memorisation test of this dialogue**.

## 5. Canonical dialogue versus semantic graph

The two are complementary.

The canonical dialogue answers:

> What is a high-quality, level-safe version of this conversation?

The semantic graph answers:

> What is each turn doing, what meanings count as success, what branches are allowed, and how do we recover when reality differs from the reference path?

Example:

```text
canonical learner line:
Can I have a coffee, please?

semantic learner intent:
request one available drink politely
```

The learner may instead say:

```text
Coffee, please.
I'd like a tea, please.
Could I get some water, please?
```

If the wording is natural enough for the level/context and completes the intent, Gemini accepts it.

## 6. Surface freedom by level

Canonical dialogue controls the baseline at every level, but Gemini's surface freedom grows with interaction complexity.

### A1

**Very close to authored language.**

- short turns
- small paraphrase range
- predictable question shapes
- little lexical improvisation
- use canonical/preferred realizations whenever the conversation remains on the normal path

Gemini may deviate when needed for a valid learner detour, clarification, correction or scenario-truth response.

### A2

**Close but more flexible.**

- natural paraphrase within familiar language
- bounded follow-ups
- small changes/preferences

### B1

**Canonical path + meaningful authored branches.**

- more surface variation
- connected responses
- realistic follow-up language

### B2–C2

**Authored discourse problem with wider surface freedom.**

We still author canonical paths/branch exemplars, but Gemini may realize the same pragmatic intent with much greater linguistic flexibility while respecting truth, level and graph.

## 7. Preferred realizations

For important AI beats, missions may include `preferred_realizations`.

Example:

```yaml
ai_intent: Ask what the learner wants to order.
preferred_realizations:
  - What would you like?
  - What can I get for you?
```

At A1, the live model should normally stay close to these reviewed realizations.

Preferred realizations are not mandatory exact strings; they are controlled surface anchors.

## 8. Listening Preview relationship

Listening Preview is authored from the **same language grounding and interaction shape**, but it should be a reviewed variant rather than a required rehearsal script.

Example:

```text
Canonical path:
Can I have a coffee, please? / Small, please.

Listening Preview variant:
I'd like a tea, please. / Large, please.
```

Both may use reviewed A1 language while demonstrating that more than one valid conversation is possible.

This gives Listening a stable quality source without teaching that the upcoming Live mission has one password dialogue.

## 9. Dynamic hints relationship

Dynamic hints remain contextual.

The model receives:

- actual conversation so far
- current semantic beat
- scenario truth
- level
- language grounding
- canonical/preferred language as support anchors

When generating useful words/full response help, Gemini should prefer level-grounded language that fits the **actual current context**.

The canonical learner line is a useful anchor, never the only valid full-help response.

## 10. Mission field shape

Recommended contract sections:

```yaml
language_grounding:
  source_repo: addvaluewithai-hub/english-course
  source_level: A1
  inventory_scope: cumulative_through_level
  abilities: []
  grammar: []
  phrases: []
  words: []
  authoring_note: selected opportunities, not mandatory learner checks

canonical_dialogue:
  purpose: reference_path_not_required_script
  turns: []

beats:
  - id: ...
    ai_intent: ...
    preferred_realizations: []
    learner_intent: ...
    accepted_semantics: []
    correction_focus: []

listening_preview:
  relationship_to_canonical: same_shape_reviewed_variant
  transcript: []

runtime:
  surface_freedom: tight | bounded | open_within_graph
```

## 11. Grounding references

When practical, store stable source IDs rather than only copied labels.

Example:

```yaml
abilities:
  - id: ability.cefr_all_descriptors.cefr.cv2020.p078.a1.obtaining_goods_and_services.002
    role: core_communicative_grounding

grammar:
  - id: egp.1741163710391x459074403345042000
    role: productive_opportunity
```

A mission does not need to tag every function word in its dialogue. Record the items that materially informed authoring, level control, correction focus or useful support.

## 12. Correction and evidence

Grounded language can influence correction focus, but it does not convert Practice into item testing.

If the canonical line is:

```text
Can I have a coffee, please?
```

then:

```text
Coffee, please.
```

may be fully valid at A1.

A genuine malformed request can be briefly corrected when it matters, but Gemini must not force the learner back to the canonical wording solely because it was authored.

Likewise, seeing a grounded grammar item in one successful mission is contextual evidence, not broad mastery.

## 13. Authoring principle

The final relationship between Learn and Practice is:

> **Learn curates and teaches the English. Practice deliberately recombines that reviewed English into authored real-world conversations. Gemini makes those conversations alive without becoming their curriculum writer.**
