---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Nocturnal HR dipping on Labs.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Vitals
  - entity: heart-rate-day
    effect: reads
    facts: &id002
    - Date
    - Readings
  actor: person
  contexts:
    personal:
      place: web::personal::labs
    public:
      place: web::public::labs
- text: The Product shows the median day-to-night drop and nights below 10 percent; at least half below 10 percent gives a pattern.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
  - entity: heart-rate-day
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
  target: src/pipeline/labs.ts#dipping
---

# Find nights with a small drop

## Trigger

The person opens the Lab. Seven qualifying finished nights are available within the last 30 finished days.

## Outcome

The card places the median drop on its bands (rise, small, typical, large) and shows how many measured nights dropped less than 10%.
