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
- text: The Product reports waiting and identifies the signals received today.
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

# Wait for today’s strain readings

## Trigger

Earlier ranges are ready but fewer than two usable readings have arrived for today.

## Outcome

The Lab waits for today and never borrows yesterday’s reading to fill a missing signal.
