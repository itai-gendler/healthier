---
kind: alternate
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Vitals.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::vitals
    public:
      place: web::public::vitals
- text: The Product shows the Vitals cards that are not on Today, cautious ones first, then fresh news, then by importance.
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
      place: web::personal::vitals
    public:
      place: web::public::vitals
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

# Read the cards on Vitals

## Trigger

The person opens Vitals.

## Outcome

Cards about vitals that are not key today stay on Vitals, so nothing shows twice.
