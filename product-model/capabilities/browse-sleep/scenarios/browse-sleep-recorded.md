---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Sleep and picks a span.
  kind: actor
  entities:
  - entity: sleep-session
    effect: reads
    facts: &id001
    - Date
    - Kind
    - Timing
    - Duration
    - Stages
    - Efficiency
    - Source
  - entity: goals
    effect: reads
    facts: &id002
    - Sleep need
  - entity: health-day
    effect: reads
    facts: &id003
    - Date
    - Vitals
  actor: person
  contexts:
    personal:
      place: web::personal::sleep
    public:
      place: web::public::sleep
- text: The Product shows the latest main sleep with its stages where recorded, keeps naps apart, and works out sleep debt and regularity from recorded nights against the sleep need.
  kind: product
  entities:
  - entity: sleep-session
    effect: reads
    facts: *id001
  - entity: goals
    effect: reads
    facts: *id002
  - entity: health-day
    effect: reads
    facts: *id003
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

# Read last night and sleep over time

## Trigger

Sleep has been recorded in the recent window.

## Outcome

Last night, the last seven nights, naps, sleep debt, the sleep window and regularity all read from the nights that were recorded.
