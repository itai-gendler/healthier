---
kind: edge
routes:
  personal: Connected profile
steps:
- text: The person confirms deletion.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle-settings
- text: The Product reports failure and retains the cycle days and cycle settings.
  kind: product
  entities:
  - entity: cycle-day
    effect: reads
    facts:
    - Date
    - Flow
    - Symptoms
    - Note
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
      place: web::personal::cycle-settings
references:
- kind: code
  role: implementation
  target: src/views/DataCards.tsx#CycleCard
- kind: code
  role: implementation
  target: src/hooks/useCycle.tsx#CycleProvider
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
---

# Keep the log when deletion fails

## Trigger

The delete request fails.

## Outcome

Deletion failure is shown and the locally displayed log is retained.
