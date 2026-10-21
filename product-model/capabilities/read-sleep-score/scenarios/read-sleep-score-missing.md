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
- text: An unstaged sleep keeps an unknown restorative percentage and receives the neutral restoration contribution rather than a zero-stage claim.
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

# Score a night without stages

## Trigger

The latest main sleep was recorded without stages.

## Outcome

The score keeps its three parts: restoration takes the midpoint rather than zero, and the deep and REM share stays unknown.
