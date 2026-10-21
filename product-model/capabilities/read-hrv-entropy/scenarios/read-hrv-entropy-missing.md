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
- text: The Product shows recent readings unjudged and collecting until both baseline and recent requirements are met.
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
  target: src/pipeline/labs.ts#entropyShift
---

# Learn the usual entropy range first

## Trigger

Fewer than ten readings in the six weeks before the last two, or fewer than seven in the last two.

## Outcome

The nights so far show unjudged, and the Lab reads as collecting.
