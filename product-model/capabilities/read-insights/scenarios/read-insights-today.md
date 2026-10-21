---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Today.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
- text: The Product runs every card on the person’s days, settles conflicts, and shows on Today each alert or nudge while it is true and anything else while it is news, for the part of the day.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Movement
    - Vitals
    - Body
    - Notifications
    - Zones
    - Sources
    - Sleeping heart rate floor
  - entity: sleep-session
    effect: reads
    facts:
    - Date
    - Kind
    - Timing
    - Duration
    - Stages
    - Efficiency
    - Source
  - entity: goals
    effect: reads
    facts:
    - Steps
    - Brisk minutes
    - Sleep need
  - entity: cycle-settings
    effect: reads
    facts:
    - Tracking
    - Today cards
    - Other pages
    - Log kept
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
references:
- kind: code
  role: implementation
  target: src/pipeline/insights/engine.ts#evaluate
- kind: code
  role: implementation
  target: src/pipeline/insights/conflicts.ts#settle
- kind: code
  role: implementation
  target: src/pipeline/insights/place.ts#place
---

# Read the cards that matter now on Today

## Trigger

The person opens Today.

## Outcome

Each card shows in one place only, as a plain sentence with the numbers it compared.
