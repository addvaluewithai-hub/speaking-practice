# Practice Sources

This repository intentionally separates **grounding sources** from **product design decisions**.

No external source directly defines the Englotti Practice mission library. We use references to calibrate level, select language, validate real-world workflow, and then author the actual conversations ourselves.

## 1. Shared Englotti English ground

Primary internal source:

- `addvaluewithai-hub/english-course`

Use it actively when authoring a mission to select and validate:

- level-bounded vocabulary
- phrases/chunks
- grammar
- communicative abilities
- productive vs receptive expectations
- pronunciation/intelligibility scope where relevant
- source provenance

Important: Practice does **not** mirror Learn lesson order and does not require Learn completion.

The shared source is not a Practice sequence, but it is more than a passive ceiling: it is the reviewed **language material from which Practice canonical dialogues should be deliberately written**.

Level inventories in `english-course` represent language newly assigned at each level, while exit expectations are cumulative. Practice authoring should therefore use reviewed language cumulatively through the mission level.

Example:

```text
A1 Practice mission
-> select relevant A1 abilities / grammar / phrases / words
-> write a level-safe canonical dialogue
-> derive/validate semantic beats and live surface bounds
```

Do not force every selected item into learner production. Grounding informs authored language and runtime control; it is not a hidden pass/fail checklist.

See `LANGUAGE_GROUNDING_AND_CANONICAL_DIALOGUE_V1.md`.

## 2. CEFR / Council of Europe

Official references:

- CEFR Companion Volume: https://www.coe.int/en/web/common-european-framework-reference-languages/cefr-companion-volume-and-its-language-versions
- CEFR descriptors: https://www.coe.int/en/web/common-european-framework-reference-languages/cefr-descriptors
- CEFR level descriptions: https://www.coe.int/en/web/common-european-framework-reference-languages/level-descriptions
- CEFR classroom / action-oriented implementation: https://www.coe.int/en/web/common-european-framework-reference-languages/cefr-in-the-classroom

Use CEFR for:

- broad level calibration
- spoken interaction expectations
- amount of independence
- interaction strategies
- qualitative aspects of spoken language
- action-oriented task thinking

Do **not** treat CEFR as a ready-made list of Practice scenarios. CEFR is a reference framework that must be adapted to the product context.

Where CEFR descriptors have already been reviewed into `english-course` abilities, prefer storing the stable internal ability ID in the mission grounding rather than duplicating unsupported free-text claims.

## 3. English Profile / learner corpus references

Optional secondary validation source for English level plausibility:

- English Profile / Cambridge research and vocabulary profiling resources

Use these only as a **cross-check** when a word, phrase, construction, or sense has uncertain level placement. They do not override reviewed internal source decisions automatically.

## 4. Real-world task research

For each world, mission authors may research the actual interaction flow from trustworthy primary or domain sources.

Examples:

- hotel check-in / booking flows
- restaurant ordering norms
- ticket purchase flows
- workplace meeting conventions
- customer-service processes

The purpose is to make the **task realistic**, not to copy dialogue text.

Research notes should record:

- source URL / title
- date accessed where relevant
- what real-world fact or workflow it informs
- whether that fact is locale-specific

Real-world research controls scenario truth/workflow. `english-course` controls language grounding. Englotti authors the actual canonical dialogue that combines the two.

## 5. Authored conversation as product work

A source-grounded mission is still an Englotti-authored object.

The authoring responsibility is:

```text
reviewed language + real interaction truth
-> canonical conversation written by us
-> semantic graph written by us
-> Listening Preview variant written by us
-> bounded Gemini performance
```

Gemini Live is not an external content source for the curriculum. Its role is performance/adaptation and runtime QA.

## 6. What is explicitly not a source of truth

The following may inspire discussion but must not constrain this new repository by default:

- old Speaking roadmaps
- old lesson counts
- old database shapes
- old scenario taxonomies
- old prompt contracts
- Learn lesson sequence as Practice sequence

If an old idea is reused, it must earn its place again under the current Practice architecture.

## Source hierarchy

When authoring a mission:

```text
1. Real communicative goal
2. CEFR interaction difficulty appropriate to level
3. Englotti shared-English reviewed inventory
4. Selected mission language grounding
5. Real-world task truth / workflow
6. Canonical authored dialogue
7. Semantic graph / branches / runtime bounds
8. Listening Preview variant where useful
9. Gemini Live performance and runtime QA
```

The final mission is an Englotti-authored product object, not a copied textbook exercise and not a conversation invented fresh by Gemini.
