---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person enters the day’s flow, symptoms or note.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
- text: The Product creates the cycle day and marks that a log is kept.
  kind: product
  entities:
  - entity: cycle-day
    effect: creates
    facts:
    - Date
    - Flow
    - Symptoms
    - Note
  - entity: cycle-settings
    effect: changes
    facts:
    - Log kept
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
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

# Log a day

## Trigger

The person chooses an unlogged day and saves at least one field.

## Outcome

The dated entry is saved and the cycle interpretation immediately reflects it.
