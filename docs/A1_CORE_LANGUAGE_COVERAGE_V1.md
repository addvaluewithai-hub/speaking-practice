# A1 Core language coverage v1

Status: **current eight-mission Core batch**

This report answers a specific authoring question:

> Which reviewed A1 language items from `addvaluewithai-hub/english-course` have we deliberately used to ground the eight current A1 Core Practice missions?

It is **not** a mastery checklist and it is not a target percentage of the whole A1 inventory.

## Counting method

Counts below use explicit stable references inside each mission's `language_grounding` block.

Items are de-duplicated by stable source ID across the eight Core missions.

We do **not** mechanically count every function word in dialogue. We also do not count `allowed_untracked_models` as separate curriculum items unless they have their own explicit grounding reference.

## Batch totals

| Grounding type | Reference occurrences across 8 missions | Unique A1 items |
| --- | ---: | ---: |
| Words | 30 | **29** |
| Phrases | 10 | **4** |
| Grammar patterns | 7 | **3** |
| Communicative ability anchors | 27 | **24** |

The difference between occurrences and unique items is intentional reuse. For example, `room`, `Thank you`, `can for requests`, and a few abilities naturally support more than one real-life mission.

## Per-mission grounding counts

| Mission | Words | Phrases | Grammar | Abilities |
| --- | ---: | ---: | ---: | ---: |
| A1-PS-01 — Meet someone new | 4 | 2 | 1 | 4 |
| A1-EV-01 — Ask someone to repeat | 3 | 2 | 1 | 3 |
| A1-FS-01 — Order a drink | 7 | 2 | 2 | 3 |
| A1-TT-01 — Ask where a place is | 3 | 2 | 0 | 4 |
| A1-TT-03 — Check into a hotel | 4 | 1 | 1 | 2 |
| A1-WS-01 — Say what you do or study | 2 | 0 | 1 | 3 |
| A1-HS-02 — Book a simple appointment | 4 | 1 | 1 | 4 |
| A1-PL-03 — Make a simple plan | 3 | 0 | 0 | 4 |

# 29 unique grounded A1 words

| Word | Stable source ID | Core mission(s) |
| --- | --- | --- |
| again | `oxford.o3000.p01.016` | EV-01 |
| bank | `oxford.o3000.p01.058` | TT-01 |
| cafe | `oxford.o3000.p01.116` | TT-01 |
| cinema | `oxford.o3000.p01.143` | PL-03 |
| coffee | `oxford.o3000.p01.154` | FS-01 |
| doctor | `oxford.o3000.p01.212` | HS-02 |
| dollar | `oxford.o3000.p01.214` | FS-01 |
| film | `oxford.o3000.p02.041` | PL-03 |
| good | `oxford.o3000.p02.086` | PS-01 |
| goodbye | `oxford.o3000.p02.087` | PS-01 |
| hello | `oxford.o3000.p02.114` | PS-01 |
| hotel | `oxford.o3000.p02.132` | TT-03 |
| key | `oxford.o3000.p02.172` | TT-03 |
| large | `oxford.o3000.p02.179` | FS-01 |
| left | `oxford.o3000.p02.186` | TT-01 |
| Monday | `oxford.o3000.p02.244` | HS-02 |
| morning | `oxford.o3000.p02.248` | HS-02 |
| name | `oxford.o3000.p02.262` | PS-01 |
| night | `oxford.o3000.p02.275` | TT-03 |
| please | `oxford.o3000.p03.077` | FS-01 |
| room | `oxford.o3000.p03.132` | EV-01, TT-03 |
| Saturday | `oxford.o3000.p03.141` | PL-03 |
| say | `oxford.o3000.p03.142` | EV-01 |
| small | `oxford.o3000.p03.183` | FS-01 |
| student | `oxford.o3000.p03.218` | WS-01 |
| tea | `oxford.o3000.p03.237` | FS-01 |
| teacher | `oxford.o3000.p03.239` | WS-01 |
| Tuesday | `oxford.o3000.p04.018` | HS-02 |
| water | `oxford.o3000.p04.054` | FS-01 |

## Canonical-dialogue relationship

**25 of the 29 grounded words appear directly in at least one of the eight canonical dialogues.**

The four grounded words that do not need to appear literally in the canonical normal path are still useful scenario/alternative anchors:

- `goodbye` — leave-taking boundary for the social mission
- `tea` — valid menu alternative in Order a drink
- `water` — valid menu alternative in Order a drink
- `hotel` — scenario/domain anchor for the check-in mission

This is healthy: grounding is allowed to constrain accepted alternatives and scenario language, not only the one canonical path.

# 4 unique grounded A1 phrases

| Phrase | Stable source ID | Core mission(s) |
| --- | --- | --- |
| How are you? | `oxford.phrase.online.0346` | PS-01 |
| excuse me | `oxford.phrase.online.0229` | EV-01, TT-01 |
| ask for sth | `oxford.phrase.online.0076` | FS-01 |
| Thank you | `oxford.phrase.online.0668` | PS-01, EV-01, FS-01, TT-01, TT-03, HS-02 |

Three of these four are literal conversational chunks that appear naturally in canonical dialogue across the batch: `How are you?`, `excuse me`, and `Thank you`.

`ask for sth` is a functional lexical grounding entry rather than a sentence learners are expected to say literally.

# 3 unique grounded A1 grammar patterns

| Grammar pattern | Stable source ID | Core mission(s) |
| --- | --- | --- |
| simple affirmative declarative clauses | `egp.1741163708329x286701804737242940` | PS-01, TT-03, WS-01 |
| can for requests | `egp.1741163710391x459074403345042000` | EV-01, FS-01, HS-02 |
| would like for wishes and preferences | `egp.1741163711300x569087712695511000` | FS-01 |

These are opportunities/bounds, not mandatory forms. For example, `Coffee, please.` remains a valid A1 order even though `can for requests` and `would like` are grounded in the mission.

# 24 unique communicative ability anchors

The eight missions contain **27 ability references**, de-duplicating to **24 unique ability anchors**.

The overlap is useful rather than accidental:

- basic social reaction supports more than one social/work-study interaction
- basic goods/services requesting supports more than one service mission
- basic time production supports both scheduling and planning

Ability grounding is what gives the missions their communicative level boundary; vocabulary alone does not define the level.

## Ability references by mission

### A1-PS-01 — Meet someone new

- self-introduction
- greeting + wellbeing reaction
- basic introduction + leave-taking
- simplest everyday polite social contact

### A1-EV-01 — Ask someone to repeat

- signal non-understanding
- express non-understanding simply
- understand concrete needs with slow/repeated support

### A1-FS-01 — Order a drink

- ask/give things
- ask for food/drink using basic expressions
- handle numbers/quantity/cost/time

### A1-TT-01 — Ask where a place is

- ask for simple directions
- understand simple directions
- understand directions when spoken slowly/clearly
- follow short simple instructions/directions

### A1-TT-03 — Check into a hotel

- check into a hotel using a few fixed expressions
- understand simple questions/instructions addressed slowly and clearly

### A1-WS-01 — Say what you do or study

- describe yourself / what you do
- say someone's job using familiar common job names
- basic social reaction

### A1-HS-02 — Book a simple appointment

- simple service request
- recognise basic times/dates
- understand prices/times/dates in familiar contexts
- tell the time to within five minutes

### A1-PL-03 — Make a simple plan

- understand basic free-time information
- understand basic questions about free time
- invite simple contributions / indicate understanding in very simple collaboration
- tell the time to within five minutes

# What this number does not mean

`29 words + 4 phrases + 3 grammar patterns` does **not** mean the learner has to produce 36 items to pass the eight missions.

Practice success remains communicative:

- did the learner order the drink?
- recover the missed detail?
- ask where the bank is and understand the direction?
- complete the simple plan?

Grounded items are the reviewed language material we deliberately used to write and constrain those conversations.

This distinction should stay intact as the library scales:

> **Use the A1 inventory to write better A1 conversations, not to turn conversation into a hidden vocabulary checklist.**
