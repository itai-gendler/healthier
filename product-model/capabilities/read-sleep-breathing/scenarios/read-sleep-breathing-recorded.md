---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Sleep-disordered breathing patterns on Labs.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Vitals
  - entity: sleep-session
    effect: reads
    facts: &id002
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
- text: The Product judges each of the last 14 nights’ oxygen, breathing rate and time awake against the four weeks before them, and shows a pattern when 3 or more had two of them off together.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
  - entity: sleep-session
    effect: reads
    facts: *id002
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

# Find nights with two signals off together

## Trigger

Fourteen measured nights in the four weeks before the last 14, and seven measured nights among the last 14.

## Outcome

The card shows how many of the last 14 nights had two or more signals off together, which signals, and everyday reasons this can happen.
