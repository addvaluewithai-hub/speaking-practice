# Practice Authoring & QA v1

This is the publication gate for reviewed authored Practice missions.

A mission is not ready because its scenario sounds useful or because Gemini can improvise a pleasant conversation. Englotti must author the normal-path conversation, ground its language, define the semantic graph, and then prove that Live adaptation preserves those decisions.

# 1. Map gate

Before writing a full mission contract, verify:

- the mission exists in the reviewed Practice Map or has been deliberately added to fill a documented gap
- it has one primary world
- it creates a real communicative problem, not a vocabulary theme disguised as a conversation
- it is meaningfully distinct from nearby missions
- its level changes the communication problem rather than only adding harder words

# 2. Source and language-grounding gate

Record or verify:

- CEFR interaction fit for the level
- relevant `english-course` communicative abilities
- selected level-appropriate grammar opportunities
- selected phrases/words that naturally belong in the situation
- productive versus receptive expectations where this affects authoring/correction
- pronunciation/performance limits where relevant
- real-world workflow/truth where the interaction depends on domain facts
- any locale-specific assumptions

For `english-course` inventories, remember that level inventories contain language newly assigned at that level while exit expectations are cumulative. Practice may therefore use reviewed language through the mission level.

Ground only language that materially informs the mission. Do not tag every function word.

Do not copy textbook dialogue as the authored mission.

# 3. Canonical-dialogue gate

Before finalizing the semantic graph, write a complete `canonical_dialogue` from opening to natural ending.

Verify:

- it is written/reviewed by Englotti rather than generated at runtime
- it sounds like a plausible real conversation
- it is safely inside the mission level
- it deliberately uses appropriate language from the selected grounding where natural
- AI turns have the right length/density for the level
- learner turns are realistic for the level
- no learner line is only there to force a vocabulary/grammar item
- the conversation reaches the mission goal naturally
- the learner could reasonably use different valid wording and still succeed

At A1, the canonical dialogue should normally be short, highly predictable and close to the language we want Gemini to use on the normal path.

# 4. Mission contract gate

Every authored mission must define:

- stable ID + revision
- level
- primary world
- Core/library status
- roles and setting
- concrete learner goal
- language grounding
- scenario truth
- canonical dialogue
- semantic conversation graph
- preferred AI realizations where useful
- learner intent for every meaningful move
- accepted semantic boundaries where useful
- correction focus
- branch/recovery rules where useful
- natural ending / completion condition
- runtime surface freedom appropriate to the level
- dynamic hint policy
- Listening Preview metadata where applicable

# 5. Canonical-dialogue / graph consistency gate

Check every canonical turn against the graph:

- each canonical AI line fulfils the authored `ai_intent`
- each canonical learner line fulfils the authored `learner_intent`
- canonical facts exist in scenario truth
- graph order matches the natural interaction
- branch logic does not contradict the normal path
- `preferred_realizations` stay consistent with the reviewed dialogue

Then test at least two plausible learner alternatives per important productive beat where useful.

The graph must preserve meaning without requiring the canonical string.

# 6. A1-specific gate

For A1, verify:

- one clear main goal
- roughly 3–6 meaningful learner moves
- short partner turns
- partner is collaborative
- information load is small
- no hidden complication is required for success
- short natural answers are accepted
- no negotiation, extended explanation, or storytelling is required
- Gemini's normal-path wording stays close to reviewed canonical/preferred language
- dynamic hints can rescue the learner without changing mission level

# 7. Dynamic hint gate

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
- useful language/full response stay inside level and preferably draw on mission grounding
- canonical learner wording may inform help but is not treated as the only answer
- full response is an example, not a password
- personal learner data is never injected

# 8. Correction gate

Test at least:

- canonical learner line -> accept
- valid alternative wording -> accept without correction
- short but natural level-appropriate answer -> accept
- genuine current-target error -> concise correction + usable form + retry when needed
- minor non-target issue with clear meaning -> do not derail the mission
- unclear meaning -> clarify rather than pretending it succeeded

The AI must not correct simply because the learner differs from the canonical dialogue or grounded phrase inventory.

# 9. Listening Preview gate

Where a preview is required or included:

- it uses the same level grounding and interaction shape as the mission
- it is a reviewed variant, not simply the live script copied verbatim unless there is a specific justified reason
- it uses different concrete choices and/or valid wording where practical
- transcript is reviewed
- audio is fixed/reviewed for the mission revision
- language is level-safe
- duration is short enough to remain orientation
- learner can skip it and still complete the mission
- listening to it creates no speaking/mastery evidence
- live mission can naturally use different wording and concrete choices

# 10. Live surface-control gate

Verify Gemini understands the distinction between:

```text
canonical dialogue = preferred normal-path language
semantic graph = meaning/branch control
Gemini = live performer/adaptive partner
```

At A1/A2 specifically, test whether Gemini unnecessarily invents harder vocabulary or longer turns when the canonical wording would work.

Deviation from canonical language is appropriate when needed for:

- a valid learner detour
- clarification
- correction
- an unavailable/impossible option
- branch handling
- scenario-truth consistency

Unmotivated stylistic improvisation that increases difficulty should be tuned out.

# 11. Adversarial conversation QA

Run every mission through:

1. canonical expected response
2. valid paraphrase
3. short valid alternative
4. grammatically wrong but understandable response
5. wrong communicative meaning
6. silence / hesitation
7. learner requests help
8. learner uses Arabic briefly
9. learner changes their mind
10. learner asks an unexpected but reasonable question
11. learner asks for something impossible under scenario truth
12. learner interrupts Gemini
13. learner goes briefly off topic
14. learner returns to mission goal
15. repeated retry with less/no support
16. natural ending

For branching missions, exercise every meaningful authored branch.

# 12. Runtime reliability gate

Verify:

- Gemini does not skip required beats
- scenario truth stays consistent
- AI turn length matches level
- Gemini stays appropriately close to canonical/preferred wording for the configured surface freedom
- learner pauses are not completed for them
- UI beat state stays synchronized with the conversation
- hint bundle matches current beat/request
- mission completion occurs only after a valid ending state
- reconnect/resume behaviour does not corrupt mission state where supported

# 13. Publication statuses

Suggested lifecycle:

```text
draft
  -> language_grounded
  -> dialogue_reviewed
  -> contract_reviewed
  -> runtime_ready
  -> live_qa
  -> pilot
  -> published
```

`pilot` means the mission is usable for controlled product testing but still being observed/tuned.

# 14. Review note

Do not bulk-promote missions because a template validates syntactically.

The important review question remains:

> Did we deliberately write a real, level-safe conversation first — and can Gemini keep it alive without replacing our curriculum decisions with its own improvisation?
