---
kind: alternate
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person reads overnight comparisons.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
- text: The Product compares the raw and cycle-adjusted judgements and retains only findings still supported.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Movement
    - Vitals
    - Body
    - Notifications
    - Zones
    - Sources
    - Sleeping heart rate floor
  - entity: cycle-day
    effect: reads
    facts:
    - Date
    - Flow
    - Symptoms
    - Note
  - entity: cycle-settings
    effect: reads
    facts:
    - Tracking
    - Today cards
    - Other pages
    - Log kept
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
references:
- kind: code
  role: implementation
  target: src/pipeline/insights/engine.ts#evaluate
- kind: code
  role: implementation
  target: src/pipeline/insights/conflicts.ts#settle
- kind: code
  role: implementation
  target: src/pipeline/insights/place.ts#place
---

# Allow for the cycle without changing measurements

## Trigger

Tracking and Other pages are on, and three cycles establish a typical shift.

## Outcome

A cycle-sensitive unusual-reading finding is suppressed if explained by the personal shift; no new alarm or altered measured number is introduced.
