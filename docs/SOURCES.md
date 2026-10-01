# Practice Sources

This repository intentionally separates **grounding sources** from **product design decisions**.

No external source directly defines the Englotti Practice mission library. We use references to bound levels and language; we author the actual missions ourselves.

## 1. Shared Englotti English ground

Primary internal source:

- `addvaluewithai-hub/english-course`

Use it to check:

- level-bounded vocabulary, phrases, grammar, and communicative language
- productive vs receptive expectations
- pronunciation/intelligibility scope
- source provenance where needed

Important: Practice does **not** mirror Learn lesson order and does not require Learn completion. The shared source is a language boundary, not a Practice syllabus.

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

## 5. What is explicitly not a source of truth

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
3. Englotti shared-English level boundary
4. Real-world task truth / workflow
5. Authored conversation blueprint
6. Gemini Live performance and runtime QA
```

The final mission is an Englotti-authored product object, not a copied textbook exercise.
