# Practice World Taxonomy v1

Practice worlds are **navigation categories**, not a hidden syllabus and not difficulty levels.

A mission has one primary world for browsing. It may carry secondary metadata later, but the primary world should answer:

> "Where in real life would I most naturally use this conversation?"

The same world appears across A1–C2. What changes with level is the **communication problem**, not the label of the world.

## 1. Everyday Life

Cross-context practical interactions that do **not** belong more naturally to another World.

Typical goals:

- ask someone to repeat / clarify
- exchange or confirm general details
- report/find a lost everyday item
- handle a short predictable phone interaction
- coordinate a shared everyday matter

### Admission rule

`everyday-life` must not become a catch-all.

Use it only when the mission's value is genuinely cross-context. If the same mission naturally belongs to food/shopping, travel, work/study, home/services, people/social, or plans/leisure, put it there instead.

Good example:

- targeted clarification that could happen anywhere -> `everyday-life`

Bad classification:

- call a hotel about a booking -> `travel-transport`, not `everyday-life`
- call an internet provider about a fault -> `home-services`, not `everyday-life`

## 2. People & Social

Interactions where **the relationship/conversation itself** is the main goal.

Typical goals:

- meet someone new
- exchange personal/social information
- keep a conversation going
- talk about experiences/interests
- react to social news
- give sensitive feedback at higher levels
- repair/mediate social misunderstandings at higher levels

Privacy rule: missions should work with fictional, chosen, or placeholder information where appropriate. Real personal disclosure is never required to succeed.

### Boundary with Plans & Leisure

Use `people-social` when connecting/maintaining the relationship is primary.

Example:

- talk about what you did at the weekend -> `people-social`

Use `plans-leisure` when coordinating/deciding an activity is primary.

Example:

- decide what to do this weekend -> `plans-leisure`

## 3. Food & Shopping

Discrete transactions around food, drink, shops, products, prices, orders, and purchase-related service.

Typical goals:

- order food/drink
- ask a price
- choose quantity/size/variant
- compare products
- exchange/return an item
- solve a wrong order/product problem
- negotiate a transaction-specific service solution at higher levels

### Boundary with Home & Services

Use `food-shopping` when the relationship is mainly a **discrete purchase/order/product transaction**.

Examples:

- wrong restaurant order
- faulty product
- disputed one-off shop charge

Use `home-services` when the interaction concerns an **ongoing provider/service relationship, appointment, repair, subscription, recurring delivery/service, or household access**.

## 4. Travel & Transport

Getting around, tickets, accommodation, stations, airports, directions, and travel-provider interactions.

Typical goals:

- ask directions
- buy/change a ticket
- identify the correct route/platform
- check into accommodation
- explain travel disruption
- change/recover a booking
- negotiate travel-provider solutions
- coordinate multi-provider travel issues at advanced levels

Travel remains its own World even when the communication function resembles a generic service complaint because learner navigation is clearer by real-life context.

## 5. Work & Study

Familiar educational and workplace communication.

A1/A2 stay concrete/routine. Higher levels add progress, collaboration, disagreement, priorities, feedback, facilitation, professional register, and complex decision-making.

Typical goals:

- say what you do/study
- ask about schedule/task/instructions
- arrange a meeting/study session
- clarify responsibilities
- give progress updates
- resolve misunderstandings
- discuss priorities/trade-offs
- give/challenge feedback
- facilitate a meeting

### Workplace/study balance

Higher-level scenarios should not silently become “work only”. When a communication problem transfers naturally, authoring may use either workplace or study/academic truth models.

Do not duplicate every mission just to create both variants; vary contexts deliberately during production.

## 6. Home & Services

Home life plus ongoing routine services that are not primarily shopping or travel.

Typical goals:

- ask for Wi-Fi/access details
- book/change an appointment
- report a household/service problem
- arrange a repair
- follow up on a delayed service/delivery
- resolve billing/subscription/service issues
- negotiate responsibility/repair paths at higher levels

Primary clue: the learner is dealing with a **continuing service/provider/household relationship**, not just buying one item.

## 7. Plans & Leisure

Invitations, activities, entertainment, outings, events, and collaborative decisions about what to do.

Typical goals:

- invite/respond
- agree day/time/place
- choose between activities
- express preferences/reasons
- re-plan when something changes
- balance competing group preferences
- manage implicit group priorities at higher levels

Primary clue: the mission goal is to **decide, organise, or repair a plan/activity**.

# Classification rules

## One primary world

Every authored mission has exactly one primary World for UI placement.

When a mission could fit more than one, classify by the **main communicative goal and real-life relationship**, not by vocabulary.

Examples:

- meet a colleague and discuss the work task -> `work-study`
- meet a new person at a party -> `people-social`
- arrange to see a film -> `plans-leisure`
- complain about shoes bought yesterday -> `food-shopping`
- complain that the internet provider still has not fixed the line -> `home-services`

## Worlds do not control level

No World is inherently beginner/advanced.

Example progression inside Food & Shopping:

```text
A1: order one drink
A2: order with preferences
B1: fix a wrong order
B2: negotiate when the straightforward fix is unavailable
C1: handle a significant complaint with tact/ambiguous expectations
C2: negotiate layered policy/fairness/face considerations with precise reformulation
```

## Avoid category inflation

Do not create a new World for one or two edge cases. Add a World only when it materially improves learner navigation across multiple levels and a meaningful mission family.

## Cross-level overlap test

Two missions may share a communication function if their real-life relationship or communication problem is meaningfully different.

But if canonical dialogue authoring shows that two missions produce nearly the same roles, truth, graph, and learner moves with only nouns swapped, merge or replace one rather than defending the taxonomy.

# Current canonical world IDs

```text
everyday-life
people-social
food-shopping
travel-transport
work-study
home-services
plans-leisure
```

See `CROSS_LEVEL_REVIEW_V1.md` for the whole-map review that informed these boundaries.
