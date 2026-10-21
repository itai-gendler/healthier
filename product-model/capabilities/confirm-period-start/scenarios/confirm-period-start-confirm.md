---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person confirms the suggested date.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
- text: The Product creates a cycle day with unspecified flow and marks that a log is kept.
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
  target: src/views/CycleView.tsx#CycleHero
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#cycleStarts
---

# Confirm a found start

## Trigger

A found current start is shown and the person confirms it.

## Outcome

The start becomes logged, outranks nearby found candidates and contributes to the person’s timing calibration.

## Edge cases

- Existing information for that day is preserved.
- A failed save restores the preceding log and shows failure.
