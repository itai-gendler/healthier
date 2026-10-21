---
kind: edge
routes:
  personal: Connected profile
steps:
- text: The person edits the logged values.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
- text: The Product restores the previous cycle day.
  kind: product
  entities:
  - entity: cycle-day
    effect: changes
    facts:
    - Date
    - Flow
    - Symptoms
    - Note
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
references:
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#DaySheet
- kind: code
  role: implementation
  target: src/hooks/useCycle.tsx#CycleProvider
---

# Undo an unsaved log edit

## Trigger

Saving an edited day fails.

## Outcome

The prior entry returns and a save failure is displayed.
