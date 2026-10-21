---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens the Lab.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::labs
    public:
      place: web::public::labs
- text: The Product shows Collecting with the nights measured so far; each daily sync adds one with no action needed.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Vitals
  - entity: heart-rate-day
    effect: reads
    facts:
    - Date
    - Readings
  actor: person
  contexts:
    personal:
      place: web::personal::labs
    public:
      place: web::public::labs
references:
- kind: code
  role: implementation
  target: src/views/LabsView.tsx#LabsView
- kind: code
  role: implementation
  target: src/pipeline/labs.ts#dipping
---

# Collect daytime heart rate

## Trigger

Fewer than seven nights in the last 30 finished days have both a measured daytime and a non-REM heart rate.

## Outcome

The Lab reads as collecting until seven nights are measured.
