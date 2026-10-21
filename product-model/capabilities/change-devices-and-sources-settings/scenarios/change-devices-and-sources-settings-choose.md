---
kind: primary
routes:
  personal: Connected profile
steps:
- text: The person supplies the preferred ordering or first choice.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::devices
- text: The Product saves source settings and reselects displayed readings.
  kind: product
  entities:
  - entity: source-settings
    effect: changes
    facts:
    - Order
    - First choices
  - entity: health-day
    effect: changes
    facts:
    - Sources
    - Sleeping heart rate floor
  - entity: sleep-session
    effect: reads
    facts:
    - Date
    - Kind
    - Timing
    - Duration
    - Stages
    - Efficiency
    - Source
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

# Choose the preferred sources

## Trigger

The person changes the global order or a reading’s first choice.

## Outcome

The new choice applies to all stored history immediately; recent sleeping-heart-rate floors follow the selected sleep times.
