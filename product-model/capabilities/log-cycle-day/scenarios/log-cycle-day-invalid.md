---
kind: validation
routes:
  personal: Connected profile
steps:
- text: The person submits an invalid day.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
- text: The Product reports the rejected save.
  kind: product
  entities: []
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
  target: src/views/CycleView.tsx#StartSheetFor
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#withDay
---

# Reject invalid day information

## Trigger

The submitted date, flow, symptoms or note fails validation.

## Outcome

No entry is created; the save is reported as failed.
