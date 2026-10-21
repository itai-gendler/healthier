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
    - Steps
    - Brisk minutes
    - Sleep need
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
- text: The Product shows recent sleep and movement with their dates, current progress and overnight comparisons. Today’s movement remains in progress.
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
  target: src/views/TodayView.tsx#TodayView
- kind: code
  role: implementation
  target: src/pipeline/insights/summary.ts
---

# Read last night and today so far

## Trigger

Sleep, movement or overnight vitals have been recorded for last night or today.

## Outcome

The Product shows recent sleep and movement with their dates, current progress and overnight comparisons. Today’s movement remains in progress.
