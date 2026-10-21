---
kind: edge
routes:
  personal: Connected profile
steps:
- text: The person changes a preference.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::devices
- text: The Product restores the earlier source settings.
  kind: product
  entities:
  - entity: source-settings
    effect: changes
    facts:
    - Order
    - First choices
    - Totals
  actor: person
  contexts:
    personal:
      place: web::personal::devices
references:
- kind: code
  role: implementation
  target: src/views/SourcesCard.tsx#SourcesCard
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
- kind: code
  role: implementation
  target: src/pipeline/sources.ts#sourceOrders
---

# Restore choices after a failed save

## Trigger

The preference request fails.

## Outcome

The earlier choices are restored and a save failure is shown.
