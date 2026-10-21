---
kind: primary
result: achieved
routes:
  demo: Demo
steps:
- text: The person chooses Demo mode.
  kind: actor
  entities: []
  actor: person
  capability: try-demo
  contexts:
    demo:
      place: web::public::welcome
- text: The Product opens Today for the demonstration profile.
  kind: product
  entities:
  - entity: profile
    effect: reads
    facts:
    - Origin
    - Age
    - Height
    - Gender
    - Theme
  actor: person
  capability: try-demo
  contexts:
    demo:
      place: web::public::today
- text: The person reads the current demonstration measurements.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Movement
    - Vitals
  actor: person
  capability: read-today
  contexts:
    demo:
      place: web::public::today
references:
- kind: code
  role: implementation
  target: src/App.tsx#App
---

# Arrive at Today in Demo mode

## Trigger

The person chooses Demo mode on the welcome view.

## Outcome

The person reads the demonstration’s current sleep, movement and overnight vitals.
