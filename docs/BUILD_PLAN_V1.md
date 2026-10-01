# Speaking Practice Build Plan v1

## Goal

Build a high-quality authored Practice library from a clean architecture before integrating it into the production app.

## Phase 1 — Foundation

Status: in progress

Create and review:

- Practice architecture
- A1–C2 level bible
- mission contract
- source policy
- world taxonomy
- authoring / QA checklist

Exit gate: we can explain exactly what makes an A1 mission different from a B1 or B2 mission without referring to a linear curriculum.

## Phase 2 — Vertical slice

Author only:

- 6 A1 missions
- 3 B1 missions

Choose missions that stress different interaction shapes, not nine versions of the same conversation.

Suggested A1 slice:

1. Meet someone new
2. Order a drink
3. Buy one item and ask the price
4. Ask where a place is
5. Hotel check-in
6. Make a simple plan

Suggested B1 slice:

1. Fix a wrong restaurant order
2. Change a hotel booking after a complication
3. Resolve a familiar workplace scheduling problem

Each mission must include:

- semantic conversation graph
- truth model
- learner intents
- Arabic intent hints
- useful-language hints
- full-help examples
- valid branch behaviour
- correction priorities
- natural ending

## Phase 3 — Runtime prototype

Compile authored mission contracts into Gemini Live session instructions and UI state.

Prove:

- Gemini follows the current beat without sounding scripted
- hints stay aligned with the learner's actual current intent
- valid alternative English is accepted
- genuine target errors get short useful correction
- branch facts remain consistent
- learner interruption works
- hesitation does not cause Gemini to steal the learner's turn
- off-path but sensible moves recover naturally
- mission endings are reliable

## Phase 4 — Real conversation QA

Test every vertical-slice mission with adversarial paths:

- exact expected response
- valid paraphrase
- grammatically wrong but understandable response
- wrong meaning
- silence / hesitation
- Arabic request for help
- hint reveal at each support level
- full-help reveal
- user changes their mind
- user asks an unexpected but reasonable question
- user interrupts Gemini
- repeated retry with hints off

Synthetic transcript tests are useful but do not replace real audio QA.

## Phase 5 — Product shell

Only after mission runtime works:

- level-aware Practice home
- default current-level filter
- Worlds navigation
- Recommended for you section
- hint preference: Auto / Tap / Off
- mission recap based on completion and support use
- replay with less support
- Explore other levels

No mandatory Practice sequence.

## Phase 6 — Expand A1 + A2/B1

Scale only after the vertical slice proves the authoring factory.

Expansion questions:

- Which worlds are underrepresented?
- Are missions too repetitive in interaction shape?
- Are A1 missions genuinely beginner-safe?
- Are B1 missions meaningfully more independent rather than merely longer?
- Does each new mission create a real communicative problem?

Do not target an arbitrary lesson count.

## Phase 7 — B2–C2

Author higher levels only after the runtime handles branching and semantic freedom well.

Higher levels should increase:

- negotiation
- trade-offs
- nuance
- learner initiative
- discourse length
- pragmatic choices
- ambiguity management
- reformulation

Do not make higher levels harder simply by adding obscure vocabulary.

## Phase 8 — Custom Practice

After authored Practice is stable, design a runtime mission generator that can create a temporary blueprint from a learner request.

Custom missions must be visibly distinct from reviewed authored missions because level calibration and QA confidence are lower.

## Phase 9 — Free Speak

Keep Free Speak simple: open conversation with no authored mission graph.

Do not force authored-mission evidence semantics onto open conversation.

## Current immediate task

Complete foundation docs, then author the **first three contrasting missions** before writing any large mission catalog:

- A1 Meet someone new
- A1 Order a drink
- B1 Change a hotel booking

Those three should expose most architectural weaknesses quickly.
