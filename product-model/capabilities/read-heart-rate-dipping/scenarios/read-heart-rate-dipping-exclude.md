---
kind: alternate
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person reads how the drop was worked out.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::labs
    public:
      place: web::public::labs
- text: The Product calculates from the qualifying finished nights and explains exclusions.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Vitals
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
  target: src/pipeline/labs.ts#dipping
---

# Leave unmeasured and unusual nights out

## Trigger

Some nights lack measured daytime heart rate or have several overnight signals off.

## Outcome

Only nights with more than 60 samples between 08:00 and 20:00 and a non-REM average contribute; today is excluded and excluded nights are counted.
