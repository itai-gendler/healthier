---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person clears every field and saves.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
- text: The Product removes the cycle day.
  kind: product
  entities:
  - entity: cycle-day
    effect: removes
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
  target: src/pipeline/cycle.ts#hasEntry
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#withDay
---

# Clear an entire logged day

## Trigger

The person removes flow, all symptoms and the note, then saves.

## Outcome

The dated entry disappears and the cycle view is recalculated.

## Edge cases

- If saving fails, the entry is restored and the failure is shown.
