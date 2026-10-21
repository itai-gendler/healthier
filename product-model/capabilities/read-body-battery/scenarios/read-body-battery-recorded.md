---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Today.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Movement
    - Vitals
    - Sources
  - entity: sleep-session
    effect: reads
    facts: &id002
    - Date
    - Kind
    - Timing
    - Duration
    - Stages
    - Efficiency
    - Source
  - entity: goals
    effect: reads
    facts: &id003
    - Sleep need
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
- text: The Product gives a score from 1 to 100 with what raised and lowered it, from recent HRV, resting heart rate and sleep, and says how confident it is.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
  - entity: sleep-session
    effect: reads
    facts: *id002
  - entity: goals
    effect: reads
    facts: *id003
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

# Read the body battery and what moved it

## Trigger

Last night's HRV, resting heart rate or sleep has been recorded.

## Outcome

The body battery lists each reading that raised or lowered it, so the score can be traced back to the readings behind it.
