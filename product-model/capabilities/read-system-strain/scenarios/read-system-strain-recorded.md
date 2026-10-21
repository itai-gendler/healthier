---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens System Strain Radar on Labs.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Vitals
  actor: person
  contexts:
    personal:
      place: web::personal::labs
    public:
      place: web::public::labs
- text: The Product marks each of the four signals off, normal or no data today, and places today at Baseline (0–1 off), Elevated (2) or High (3–4).
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
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

# Count the signals off today

## Trigger

The person opens the Lab. At least two signals have eight earlier readings in the preceding 28 days and readings on the latest day.

## Outcome

Elevated or High names the signals that are off together and everyday reasons several can move at once.
