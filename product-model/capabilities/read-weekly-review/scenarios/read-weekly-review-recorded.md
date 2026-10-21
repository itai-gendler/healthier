---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person reads This week on Today.
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
- text: 'The Product shows seven days ending today: each morning’s body battery, average recorded sleep, active minutes including today so far, and average steps and goal-reaching days from finished days only. Missing figures remain absent.'
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

# Read This week

## Trigger

The person opens Today with recorded days.

## Outcome

The Product shows seven days ending today: each morning’s body battery, average recorded sleep, active minutes including today so far, and average steps and goal-reaching days from finished days only. Missing figures remain absent.

## Edge cases

- Active Zone Minutes supply the period’s activity total when any are recorded; otherwise brisk minutes count vigorous minutes twice.
- Sleep reports how many nights contribute when coverage is incomplete.
