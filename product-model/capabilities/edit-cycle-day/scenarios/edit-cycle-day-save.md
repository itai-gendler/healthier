---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person changes the logged values.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
- text: The Product replaces the cycle day facts.
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
    public:
      place: web::public::cycle
references:
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#DaySheet
- kind: code
  role: implementation
  target: src/hooks/useCycle.tsx#CycleProvider
---

# Edit a logged day

## Trigger

The person opens a logged date and saves changed fields.

## Outcome

The date has one updated entry and the derived cycle view recomputes.
