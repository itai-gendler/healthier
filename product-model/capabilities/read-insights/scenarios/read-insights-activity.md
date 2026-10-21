---
kind: alternate
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Activity.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::activity
    public:
      place: web::public::activity
- text: The Product shows the Activity cards that are not on Today, cautious ones first, then fresh news, then by importance.
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
      place: web::personal::activity
    public:
      place: web::public::activity
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

# Read the cards on Activity

## Trigger

The person opens Activity.

## Outcome

Cards about activity that are not key today stay on Activity, so nothing shows twice.
