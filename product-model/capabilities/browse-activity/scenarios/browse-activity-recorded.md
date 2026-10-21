---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Activity and picks a span, from the recent window to all stored history.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Movement
    - Sources
  - entity: goals
    effect: reads
    facts: &id002
    - Steps
    - Brisk minutes
  actor: person
  contexts:
    personal:
      place: web::personal::activity
    public:
      place: web::public::activity
- text: The Product shows today so far and the last seven days against the step and brisk-minute goals, averages finished days only, and groups longer spans into weekly or monthly averages per recorded day.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
  - entity: goals
    effect: reads
    facts: *id002
  actor: person
  contexts:
    personal:
      place: web::personal::activity
    public:
      place: web::public::activity
references:
- kind: code
  role: implementation
  target: src/views/ActivityView.tsx#ActivityView
- kind: code
  role: implementation
  target: src/views/ActivityCards.tsx
- kind: code
  role: implementation
  target: src/ui/span.tsx#useSpan
---

# Read movement against goals over a chosen span

## Trigger

The person opens Activity with steps recorded in the recent window.

## Outcome

Progress reads against the person's own goals and the WHO's 150 minutes a week. Today counts as in progress, so averages and comparisons read finished days.
