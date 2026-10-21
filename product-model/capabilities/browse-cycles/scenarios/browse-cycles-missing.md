---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Cycle.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
- text: Until the nights or a logged period show a cycle, the Product says it is still finding the rhythm; after 90 recorded nights in the last 120 with no cycle found, it says none has stood out yet and that a logged period would show one.
  kind: product
  entities:
  - entity: cycle-day
    effect: reads
    facts:
    - Date
    - Flow
    - Symptoms
    - Note
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Vitals
    - Sleeping heart rate floor
    - Sources
  - entity: cycle-settings
    effect: reads
    facts:
    - Tracking
    - Today cards
    - Other pages
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
  target: src/views/CycleView.tsx#CycleView
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#summarizeCycles
- kind: code
  role: implementation
  target: src/pipeline/cyclePhases.ts#cycleShape
---

# Keep looking for the rhythm

## Trigger

Cycle tracking is on, nothing is logged, and the nights have not shown a cycle.

## Outcome

The page reads as collecting, or says no cycle has been found yet; it never shows a cycle the nights do not support.
