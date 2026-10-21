---
kind: edge
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
- text: The Product marks HRV or resting heart rate as calibrating to a new device instead of missing.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Vitals
    - Sources
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
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
references:
- kind: code
  role: implementation
  target: src/views/BodyBattery.tsx
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#readiness
---

# Wait for a new device baseline

## Trigger

Recent HRV or resting heart rate comes from a device without its own sufficient baseline.

## Outcome

That contribution is identified as calibrating; other usable core signals can still support a lower-confidence score.
