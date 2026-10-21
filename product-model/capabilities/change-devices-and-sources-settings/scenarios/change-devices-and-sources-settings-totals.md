---
kind: alternate
routes:
  personal: Connected profile
steps:
- text: The person confirms the change to totals.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::devices
- text: The Product saves source settings and starts replacement synchronization.
  kind: product
  entities:
  - entity: source-settings
    effect: changes
    facts:
    - Totals
  - entity: health-day
    effect: changes
    facts:
    - Movement
    - Sleeping heart rate floor
  - entity: heart-rate-day
    effect: removes
  - entity: synchronization
    effect: changes
    facts:
    - Progress
    - Failure
    from: Ready
    to: Running
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

# Change what counts in daily totals

## Trigger

The person chooses a different total-source family and confirms the refetch.

## Outcome

Totals and minute heart rate are cleared and re-fetched with the new family; a running sync finishes before that refetch starts.

## Edge cases

- Cancelling the refetch confirmation preserves the current choice.
