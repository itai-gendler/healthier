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
- text: The Product shows Collecting with the nights measured so far and how many it needs, and judges none of them yet.
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

# Learn the usual nights first

## Trigger

Fewer than 14 measured nights in the four weeks before the last 14, or fewer than 7 among the last 14.

## Outcome

The Lab reads as collecting, never as nothing found.
