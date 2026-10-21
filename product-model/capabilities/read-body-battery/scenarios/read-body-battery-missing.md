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
- text: The Product shows no score when none of last night's HRV, resting heart rate and sleep is usable, and names the ones that are missing.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Movement
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
  - entity: goals
    effect: reads
    facts:
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
  target: src/views/BodyBattery.tsx
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#readiness
---

# Give no score without last night's signals

## Trigger

None of HRV, resting heart rate or sleep has a usable reading for last night.

## Outcome

The body battery shows no score yet and says what is missing; it never scores from older nights.
