---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens the heart rate chart on Vitals.
  kind: actor
  entities:
  - entity: heart-rate-day
    effect: reads
    facts: &id001
    - Date
    - Readings
  - entity: health-day
    effect: reads
    facts: &id002
    - Date
    - Zones
  actor: person
  contexts:
    personal:
      place: web::personal::vitals
    public:
      place: web::public::vitals
- text: The Product starts on the latest 24 hours; moving through time or changing the interval updates the lowest, average and highest heart rate and the zones for the minutes in view.
  kind: product
  entities:
  - entity: heart-rate-day
    effect: reads
    facts: *id001
  - entity: health-day
    effect: reads
    facts: *id002
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

# Explore heart rate minute by minute

## Trigger

Minute heart rate has been recorded in the recent window.

## Outcome

The person reads heart rate across the retained window, one average per minute, against their own zones.
