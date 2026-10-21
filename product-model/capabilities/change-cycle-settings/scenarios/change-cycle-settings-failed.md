---
kind: edge
routes:
  personal: Connected profile
steps:
- text: The person changes tracking preferences.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle-settings
- text: The Product restores the prior cycle settings.
  kind: product
  entities:
  - entity: cycle-settings
    effect: changes
    facts:
    - Tracking
    - Today cards
    - Other pages
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

# Restore cycle settings after failed save

## Trigger

The settings save fails.

## Outcome

The change is undone and the failure is shown.
