---
kind: alternate
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
- text: The Product places the median drop in the typical or large band, with how many measured nights dropped less than 10%.
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

# Read a typical or large drop

## Trigger

Seven measured nights in the last 30 finished days, fewer than half of them dropping less than 10%.

## Outcome

The Lab shows the drop it measured and the nights behind it; this is not an all-clear.
