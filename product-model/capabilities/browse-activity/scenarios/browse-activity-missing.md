---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Activity.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::activity
    public:
      place: web::public::activity
- text: The Product says there is no movement data and points to the list of streams in Settings, instead of showing zero steps.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Movement
    - Sources
  - entity: goals
    effect: reads
    facts:
    - Steps
    - Brisk minutes
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

# Show Activity with no movement recorded

## Trigger

No steps have been recorded, in the recent window or in stored history.

## Outcome

Activity explains that nothing has arrived and where to look; a missing day is never shown as zero.
