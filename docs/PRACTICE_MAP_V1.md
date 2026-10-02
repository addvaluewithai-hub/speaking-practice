# Practice Map v1

This document is the **master library-map index**, not a linear curriculum.

Detailed level maps live in `docs/practice-map/` so A1–C2 can be reviewed without turning one file into a giant document.

The map answers:

> Which real-life conversations should an Englotti learner be able to choose from at each level, and how does the communication problem become richer across levels?

A mission appearing in a level map is a design commitment to a real communicative problem. It is **not yet a published mission** until its full contract, language grounding, authored canonical dialogue, semantic graph, runtime behaviour, Listening Preview where useful/required, and Live QA pass review.

There is no mandatory order inside a level.

`Core` means **Great place to start**, not prerequisite.

## Current level-map status

| Level | Status | File |
| --- | --- | --- |
| A1 | first full map drafted | `practice-map/A1.md` |
| A2 | first full map drafted | `practice-map/A2.md` |
| B1 | next mapping pass | `practice-map/B1.md` when drafted |
| B2 | pending | `practice-map/B2.md` when drafted |
| C1 | pending | `practice-map/C1.md` when drafted |
| C2 | pending | `practice-map/C2.md` when drafted |

Existing B1 app experiments may inform runtime research, but they do not define the new Practice map.

## Map design rules

Every mapped mission must:

- solve a plausible real-world communicative problem
- have one primary World
- fit the interaction difficulty of its CEFR level
- be meaningfully distinct from nearby missions
- avoid becoming a vocabulary theme disguised as conversation
- state why a repeated context is harder/easier than the same context at another level
- remain independently enterable; no hidden lesson prerequisite

Mission counts are a result of useful coverage, not a target.

## Cross-level difficulty rule

Do not make progression by mechanically adding harder vocabulary or longer sentences.

The **communication problem itself** should change.

Example:

```text
A1: order one item
A2: order with preferences
B1: resolve a wrong order
B2: negotiate a service solution under constraints
C1: handle a sensitive complaint with tact
C2: mediate layered positions and reformulate precisely
```

The same real-world world/context may therefore return at several levels as separate authored missions.

## Relationship to the shared English curriculum

Practice map design uses `addvaluewithai-hub/english-course` as the reviewed shared-English source of truth for:

- communicative abilities
- level-bounded vocabulary/phrases
- grammar
- pronunciation/performance expectations where relevant

At map stage these sources help validate that the **type of interaction** belongs at the level.

When a mission is promoted to a full contract, authors select explicit source IDs and deliberately write the mission's canonical conversation from level-appropriate reviewed language.

The inventories are authoring material and level control, not hidden learner checklists.

## Coverage review

Each level file contains its own coverage matrix.

Across the full map we also review whether progression develops a balanced range of needs such as:

- social interaction
- asking/giving information
- requests and transactions
- preferences and comparisons
- arrangements
- clarification/repair
- describing/explaining
- past experience/narration
- problem solving
- negotiation/trade-offs
- disagreement
- pragmatic tact/register
- reformulation/mediation

Not every category must appear equally at every level. Some interaction needs only become appropriate at B1+.

## Map-to-mission production rule

For each mission promoted from the map into `missions/`:

1. Validate the real-world communicative goal and workflow.
2. Select relevant reviewed language from `english-course` and record stable source IDs.
3. Write the complete **canonical authored dialogue** from opening to natural ending.
4. Review the canonical dialogue for level, realism, turn length, density, and language control.
5. Define compact scenario truth.
6. Author/validate the semantic graph around the dialogue: AI intents, learner intents, accepted meanings, branches, and recovery paths.
7. Add preferred AI realizations and runtime surface-freedom bounds appropriate to the level.
8. Define correction focus and dynamic contextual Hint behaviour.
9. Write the Listening Preview as a reviewed variant where required/useful.
10. Add adversarial QA cases and run real Gemini Live/audio QA before `published` status.

Core rules:

> **We write the conversation. Gemini performs and adapts it.**

> **We author the intent. Gemini authors the contextual help.**

See:

- `LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md`
- `MISSION_CONTRACT_V1.md`
- `AUTHORING_QA_V1.md`

## Next mapping pass

With A1 and A2 now visible, the next task is **B1**.

B1 must introduce genuinely more independent familiar communication:

- meaningful complications
- connected explanation rather than isolated details
- learner-owned follow-ups
- short narration/explanation stretches
- multiple plausible branches
- realistic problem solving

The B1 pass should use A1/A2 as explicit contrast so it does not collapse into “A2 with longer sentences.”
