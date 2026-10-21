---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Devices and sources in Settings.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::devices
    public:
      place: web::public::devices
- text: The Product says nothing has been reported yet.
  kind: product
  entities:
  - entity: data-source
    effect: reads
    facts:
    - Name
    - Last seen
    - Readings
    - Included
  - entity: source-settings
    effect: reads
    facts:
    - Order
    - First choices
    - Totals
  actor: person
  contexts:
    personal:
      place: web::personal::devices
    public:
      place: web::public::devices
references:
- kind: code
  role: implementation
  target: src/views/SourcesCard.tsx#SourcesCard
- kind: code
  role: implementation
  target: server/sync.ts#describeSources
---

# Show Devices and sources before anything is reported

## Trigger

No device or app has reported a reading yet.

## Outcome

The section says nothing has been reported yet and offers no order to choose.
