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
- text: The Product shows Collecting until two of the signals have eight readings in the four weeks before today.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Vitals
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
  target: src/pipeline/labs.ts#strainToday
---

# Learn the usual ranges first

## Trigger

Fewer than two signals have eight readings in the four weeks before today.

## Outcome

The Lab reads as collecting rather than placing today at Baseline.
