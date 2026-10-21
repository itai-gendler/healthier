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
- text: The Product reports no pattern, with how many nights had one or two signals off, and notes that one signal on its own doesn’t count.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Vitals
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
  target: src/pipeline/labs.ts#sdbScreen
---

# Report no pattern in the last 14 nights

## Trigger

Enough nights are measured, and fewer than 3 of the last 14 had two signals off together.

## Outcome

The Lab says what it watched and what it found; a quiet card is not an all-clear.
