---
kind: alternate
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person selects Month.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Movement
    - Vitals
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
    facts:
    - Steps
    - Sleep need
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
- text: The Product shows thirty days ending today and allows reading each morning’s body battery. Activity is expressed as an average week against the 150-minute guideline; sleep and completed-day step comparisons use the same rules as the week.
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
    facts:
    - Steps
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
  target: src/views/ThisWeek.tsx
- kind: code
  role: implementation
  target: src/pipeline/insights/summary.ts
---

# Read This month

## Trigger

The person selects Month in This week.

## Outcome

The Product shows thirty days ending today and allows reading each morning’s body battery. Activity is expressed as an average week against the 150-minute guideline; sleep and completed-day step comparisons use the same rules as the week.
