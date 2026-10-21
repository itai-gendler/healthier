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
- text: The Product shows missing recent measurements instead of presenting readings older than yesterday as current.
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
    - Steps
    - Brisk minutes
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
  target: src/views/TodayView.tsx#TodayView
- kind: code
  role: implementation
  target: src/pipeline/insights/summary.ts
---

# Show what has not arrived

## Trigger

Nothing has synced for last night or the night before, or no steps today or yesterday.

## Outcome

Today says what has not arrived rather than presenting an older reading as current.
