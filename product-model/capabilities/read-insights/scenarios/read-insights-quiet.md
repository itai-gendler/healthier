---
kind: alternate
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
- text: The Product brings forward still-true eligible findings without placing opposing family tones together.
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

# Bring cards forward to a quiet Today

## Trigger

Fewer than two findings are currently selected for Today.

## Outcome

Eligible page findings move to Today, cautious first, until it has two where possible; moved findings disappear from their subject feeds.
