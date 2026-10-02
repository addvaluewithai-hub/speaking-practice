# Listening Preview v1

Listening Preview is an **optional orientation layer** before an authored Practice mission.

It answers:

> "What could a conversation like this sound like?"

It is not the script the learner is expected to reproduce.

## Product rule

The learner can always start the live mission directly.

Listening Preview must never become a prerequisite for Practice completion.

Suggested UI:

```text
Start conversation
🎧 Hear an example first
```

Learner-facing framing should make the relationship clear:

> One possible version of this situation.

Avoid labels that imply the live conversation will repeat the same dialogue.

## Why it exists

At lower levels, a learner may understand the mission goal but still lack a mental model for the interaction:

- how the other person is likely to open
- what kinds of short questions may follow
- when the exchange naturally ends
- what a realistic turn length sounds like

The preview lowers uncertainty without turning the live mission into sentence recall.

## Content model

A Listening Preview is **authored and fixed for the mission revision**.

It should have:

- one plausible version of the same real-world situation
- level-appropriate wording
- a different concrete path from the live mission where useful
- two speakers when the situation naturally requires them
- a natural opening and ending
- a reviewed transcript
- fixed generated audio or reviewed recorded audio
- optional transcript reveal in the UI

The transcript is hidden by default unless product testing shows otherwise.

## Do not leak the live mission

The preview must teach the **shape of the interaction**, not a password answer sequence.

Example mission: `Order a drink`.

Possible preview:

```text
Cashier: Hi. What can I get for you?
Customer: Can I have a tea, please?
Cashier: Sure. Small or large?
Customer: Large, please.
Cashier: That's three dollars.
Customer: Okay, thanks.
```

The live mission may use different wording, a different drink, a different size, or a valid learner detour.

Listening Preview does not change these Practice rules:

- valid alternative learner English remains valid
- Gemini follows the authored semantic graph, not the preview transcript
- dynamic hints are generated from the actual live conversation
- listening to the preview does not count as independent speaking evidence

## Recommended length

Default target:

- A1: 20–35 seconds
- A2: 25–40 seconds
- B1: 30–45 seconds when useful
- B2+: only when the interaction pattern benefits from an exemplar; avoid adding previews by habit

The preview should stop once the learner understands the conversational shape. It is not a mini listening lesson.

## Level policy

### A1

Required content asset for **Core / Great place to start** missions before full publication.

Strongly recommended for other missions when the situation is unfamiliar or the interaction pattern is not obvious.

### A2

Recommended for Core missions and selected unfamiliar service/social patterns.

### B1

Optional. Use when the scenario has a useful interaction shape to model, not simply because every mission needs an audio clip.

### B2–C2

Selective. Higher-level difficulty often includes entering a less predictable interaction independently, so a preview should have a clear product reason.

## Mission contract shape

Optional field:

```yaml
listening_preview:
  status: authored
  purpose: orientation_not_rehearsal
  transcript:
    - speaker: ai_role
      text: Hi. What can I get for you?
    - speaker: customer
      text: Can I have a tea, please?
  audio_asset: null
  transcript_default: hidden
```

`audio_asset: null` is acceptable during authoring. Publication QA can require the asset where the level policy says the preview is required.

## Audio production

The transcript should be approved first. Audio can then be generated as a fixed asset with level-appropriate delivery.

Do not generate a new preview dynamically on every play. The point of this layer is controlled input quality and predictable level calibration.

## Evidence and telemetry

Useful product telemetry:

```text
preview_started
preview_completed
preview_transcript_opened
mission_started_after_preview
mission_started_without_preview
```

Do not treat preview completion as mission progress or speaking ability evidence.

## QA questions

Before publishing a preview, verify:

- Does it sound like a plausible version of the mission?
- Is the language safely inside the mission level?
- Does it demonstrate interaction shape without revealing one mandatory live script?
- Is it short enough to remain optional orientation?
- Would a learner who skips it lose no required instruction?
- Does the live mission still work with different wording and branches?
