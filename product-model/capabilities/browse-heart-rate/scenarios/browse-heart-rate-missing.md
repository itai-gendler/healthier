---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person moves the heart rate chart to an interval without readings.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::vitals
    public:
      place: web::public::vitals
- text: The Product shows no lowest, average or highest for an interval with no readings, and draws gaps as gaps.
  kind: product
  entities:
  - entity: heart-rate-day
    effect: reads
    facts:
    - Date
    - Readings
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Zones
  actor: person
  contexts:
    personal:
      place: web::personal::vitals
    public:
      place: web::public::vitals
references:
- kind: code
  role: implementation
  target: src/views/HeartRateCard.tsx#HeartRateCard
- kind: code
  role: implementation
  target: src/charts/heartRate.ts
---

# Leave gaps in heart rate as gaps

## Trigger

Part of the chosen interval has no minute readings.

## Outcome

Missing minutes are never joined up or filled in.
