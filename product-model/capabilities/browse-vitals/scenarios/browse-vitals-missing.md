---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Vitals.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::vitals
    public:
      place: web::public::vitals
- text: A measure with fewer than eight earlier readings from its source shows its value without calling it usual or unusual.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Vitals
    - Sources
  actor: person
  contexts:
    personal:
      place: web::personal::vitals
    public:
      place: web::public::vitals
references:
- kind: code
  role: implementation
  target: src/views/VitalsView.tsx#VitalsView
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#compareToBaseline
---

# Give no verdict without enough readings

## Trigger

A measure has too few earlier readings to set a usual range.

## Outcome

The reading is shown without a verdict until a usual range exists.
