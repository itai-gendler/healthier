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
- text: The Product reports no stretch, with how many nights were scanned.
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

# Report no stretch on measured nights

## Trigger

At least one night or nap has minute readings covering half of it, and no stretch was found.

## Outcome

The Lab says how many nights it scanned and that it found none; this is not an all-clear.
