# Practice World Taxonomy v1

Practice worlds are **navigation categories**, not a hidden syllabus and not difficulty levels.

A mission has one primary world for browsing. It may carry secondary metadata later, but the primary world should answer a simple learner question:

> "Where in real life would I most naturally use this conversation?"

The same world appears across A1–C2. What changes with level is the **communication problem**, not the label of the world.

## 1. Everyday Life

Short practical interactions that do not belong more naturally to a specialist context.

Typical goals:

- ask someone to repeat or slow down
- exchange contact details
- check a time
- ask for simple help
- confirm a basic detail

This world is also the natural home for beginner conversation-control missions when the skill is broadly reusable.

## 2. People & Social

Meeting people, maintaining light social contact, and talking about people in familiar contexts.

Typical goals:

- meet someone new
- exchange basic personal information
- introduce another person
- talk about interests and preferences
- react to simple social news
- maintain and close a social exchange

Do not turn this world into a personal-data test. Missions should work with fictional, chosen, or placeholder information where appropriate.

## 3. Food & Shopping

Transactions around food, drink, shops, products, prices, choices, and routine service encounters.

Typical goals:

- order food or drink
- ask a price
- choose size / colour / quantity
- ask whether something is available
- solve a wrong-order or product problem at higher levels
- negotiate alternatives at higher levels

## 4. Travel & Transport

Getting around, tickets, accommodation, stations, airports, directions, and routine travel services.

Typical goals:

- ask where a place is
- buy a ticket
- identify the correct bus / train / platform
- check into accommodation
- explain a travel problem
- change a booking
- negotiate a travel/service solution at higher levels

## 5. Work & Study

Familiar educational and workplace communication. A1/A2 missions stay concrete and routine; higher levels can add collaboration, priorities, disagreement, explanation, and professional register.

Typical goals:

- say what you do or study
- ask about a schedule, room, or task
- ask for simple help
- arrange a meeting or study time
- clarify responsibilities
- discuss project priorities
- handle a workplace misunderstanding

## 6. Home & Services

Home life plus routine service interactions that are not primarily shopping/travel.

Typical goals:

- ask for Wi-Fi / access details
- book a simple appointment
- report a simple household or service problem
- ask about facilities
- arrange a repair
- handle customer-service follow-up at higher levels

## 7. Plans & Leisure

Invitations, hobbies, social plans, entertainment, activities, and choosing what to do.

Typical goals:

- ask about hobbies or free time
- invite someone
- accept or decline simply
- agree a day / time / place
- compare activity options
- discuss preferences and reasons
- negotiate plans and trade-offs at higher levels

# Classification rules

## One primary world

Every authored mission must have exactly one primary world for UI placement.

When a mission could fit more than one world, classify by the **main communicative goal**, not by individual vocabulary.

Example:

- "Meet a colleague and say what you do" -> `work-study`
- "Meet a new person at a party" -> `people-social`
- "Arrange to see a film" -> `plans-leisure`

## Worlds do not control level

Do not assume some worlds are beginner and others are advanced.

Example progression inside Food & Shopping:

```text
A1: order one drink
A2: order with preferences
B1: fix a wrong order
B2: negotiate an alternative under constraints
C1: handle a sensitive service complaint with tact
C2: mediate a complex service dispute where positions and implications matter
```

## Avoid category inflation

Do not create a new world just because one or two missions feel slightly different. Add a world only when it improves learner navigation across multiple levels and a meaningful group of missions.

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
