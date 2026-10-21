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
- text: The Product shows Baseline and which of today’s readings are inside the usual range; one signal off on its own does not count.
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

# Read a baseline day

## Trigger

Usual ranges are ready, at least two of today’s signals have arrived, and at most one is off.

## Outcome

Today sits at Baseline; this is not an all-clear.
