---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Sleep.
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
  actor: person
  contexts:
    personal:
      place: web::personal::sleep
    public:
      place: web::public::sleep
- text: The Product shows the total and its duration, restoration and efficiency contributions, with the share of deep and REM sleep when staged.
  kind: product
  entities:
  - entity: sleep-session
    effect: reads
    facts: *id001
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
  target: src/pipeline/sleep.ts#scoreSleep
---

# Read the sleep score and its parts

## Trigger

The latest main sleep has been recorded.

## Outcome

The Product shows the total and its duration, restoration and efficiency contributions, with the share of deep and REM sleep when staged.
