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
- text: The Product reports collecting when no session has enough coverage; it does not report no stretches from unmeasured sleep.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
  - entity: sleep-session
    effect: reads
    facts:
    - Date
    - Kind
    - Timing
    - Duration
    - Stages
    - Efficiency
    - Source
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
  target: src/pipeline/labs.ts#nocturnalTachycardia
---

# Collect measured nights

## Trigger

No night or nap has minute readings covering half of it.

## Outcome

The Lab reads as collecting rather than none found.
