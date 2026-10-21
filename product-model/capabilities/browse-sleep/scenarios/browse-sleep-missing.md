---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Sleep.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::sleep
    public:
      place: web::public::sleep
- text: The Product shows a night with no record as empty, never as zero sleep, and leaves it out of averages.
  kind: product
  entities:
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
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Vitals
  actor: person
  contexts:
    personal:
      place: web::personal::sleep
    public:
      place: web::public::sleep
references:
- kind: code
  role: implementation
  target: src/views/SleepView.tsx#SleepView
- kind: code
  role: implementation
  target: src/views/SleepCards.tsx
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#sleepDebt
---

# Leave a missing night out

## Trigger

Some nights in the chosen span have no sleep recorded.

## Outcome

Averages, debt and regularity use recorded nights only; regularity waits for five recorded nights in a row.
