---
kind: alternate
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person selects the period-start date.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
- text: The Product creates the cycle day with unspecified flow and marks that a log is kept.
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

# Log a period start without a flow rating

## Trigger

The person chooses My period started and selects a day.

## Outcome

The day records a period start even if heaviness was not supplied; an existing day preserves its symptoms and note.
