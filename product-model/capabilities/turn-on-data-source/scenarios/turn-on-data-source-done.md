---
kind: primary
routes:
  personal: Connected profile
steps:
- text: The person changes inclusion for this source.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::devices
- text: The Product changes the data source inclusion.
  kind: product
  entities:
  - entity: data-source
    effect: changes
    facts:
    - Included
    from: 'Off'
    to: 'On'
  - entity: health-day
    effect: changes
    facts:
    - Sources
    - Sleeping heart rate floor
  actor: person
  contexts:
    personal:
      place: web::personal::devices
references:
- kind: code
  role: implementation
  target: src/views/SourcesCard.tsx#SourceRow
- kind: code
  role: implementation
  target: src/pipeline/sources.ts#sourceOrders
---

# Turn on data source

## Trigger

The person switches this source on.

## Outcome

Displayed readings are reselected across history using the revised inclusion choice.

## Edge cases

- Failure to save restores the previous inclusion and reports the failure.
