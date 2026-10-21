---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person rejects the suggested start.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
- text: The Product creates a rejected start and marks that a log is kept.
  kind: product
  entities:
  - entity: rejected-start
    effect: creates
    facts:
    - Date
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
  target: src/pipeline/cycle.ts#withRejected
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#cycleStarts
---

# Reject a found start

## Trigger

The person chooses that the found start was not a period.

## Outcome

Found starts within two days of the rejected date are excluded when the cycle summary is recomputed.

## Edge cases

- A failed save restores the prior rejection list and shows failure.
