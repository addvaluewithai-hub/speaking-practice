# Practice Authoring & QA v1

This is the publication gate for reviewed authored Practice missions.

A mission is not ready because its dialogue sounds nice. It must preserve level calibration, a real communicative goal, authored control, semantic freedom, contextual help, and reliable Live behaviour.

# 1. Map gate

Before writing a full mission contract, verify:

- the mission exists in the reviewed Practice Map or has been deliberately added to fill a documented gap
- it has one primary world
- it creates a real communicative problem, not a vocabulary theme disguised as a conversation
- it is meaningfully distinct from nearby missions
- its level changes the communication problem rather than only adding harder words

# 2. Source gate

Record or verify:

- CEFR interaction fit for the level
- Englotti shared-English level boundary
- real-world workflow/truth where the interaction depends on domain facts
- any locale-specific assumptions

Do not copy textbook dialogue as the authored mission.

# 3. Mission contract gate

Every authored mission must define:

- stable ID + revision
- level
- primary world
- Core/library status
- roles and setting
- concrete learner goal
- scenario truth
- semantic conversation graph
- learner intent for every meaningful move
- correction focus
- branch/recovery rules where useful
- natural ending / completion condition
- runtime freedom appropriate to the level
- dynamic hint policy
- Listening Preview metadata where applicable

# 4. A1-specific gate

For A1, verify:

- one clear main goal
- roughly 3–6 meaningful learner moves
- short partner turns
- partner is collaborative
- information load is small
- no hidden complication is required for success
- short natural answers are accepted
- no negotiation, extended explanation, or storytelling is required
- dynamic hints can rescue the learner without changing mission level

# 5. Dynamic hint gate

Test Hint after:

- normal expected path
- a valid learner detour
- an unavailable option
- a clarification exchange
- hiding and reopening the same hint

Verify:

- one model request returns the whole hint bundle
- later reveal levels use the cached bundle
- a hint request never advances the beat
- stale responses are rejected
- help fits the actual conversation now
- full response is an example, not a password
- personal learner data is never injected

# 6. Correction gate

Test at least:

- valid alternative wording -> accept without correction
- short but natural level-appropriate answer -> accept
- genuine current-target error -> concise correction + usable form + retry when needed
- minor non-target issue with clear meaning -> do not derail the mission
- unclear meaning -> clarify rather than pretending it succeeded

The AI must not correct simply because the learner differs from an example.

# 7. Listening Preview gate

Where a preview is required or included:

- it is one plausible version, not the live script
- transcript is reviewed
- audio is fixed/reviewed for the mission revision
- language is level-safe
- duration is short enough to remain orientation
- learner can skip it and still complete the mission
- listening to it creates no speaking/mastery evidence
- live mission can naturally use different wording and concrete choices

# 8. Adversarial conversation QA

Run every mission through:

1. expected natural response
2. valid paraphrase
3. grammatically wrong but understandable response
4. wrong communicative meaning
5. silence / hesitation
6. learner requests help
7. learner uses Arabic briefly
8. learner changes their mind
9. learner asks an unexpected but reasonable question
10. learner asks for something impossible under scenario truth
11. learner interrupts Gemini
12. learner goes briefly off topic
13. learner returns to mission goal
14. repeated retry with less/no support
15. natural ending

For branching missions, exercise every meaningful authored branch.

# 9. Runtime reliability gate

Verify:

- Gemini does not skip required beats
- scenario truth stays consistent
- AI turn length matches level
- learner pauses are not completed for them
- UI beat state stays synchronized with the conversation
- hint bundle matches current beat/request
- mission completion occurs only after a valid ending state
- reconnect/resume behaviour does not corrupt mission state where supported

# 10. Publication statuses

Suggested lifecycle:

```text
draft
  -> contract_reviewed
  -> runtime_ready
  -> live_qa
  -> pilot
  -> published
```

`pilot` means the mission is usable for controlled product testing but still being observed/tuned.

# 11. Review note

Do not bulk-promote missions because a template validates syntactically.

The important review question remains:

> Does this feel like a real conversation a learner at this level can genuinely handle, with enough authored control to be teachable/reliable and enough semantic freedom to feel alive?
