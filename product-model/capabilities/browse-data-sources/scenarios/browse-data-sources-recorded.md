---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Devices and sources in Settings.
  kind: actor
  entities:
  - entity: data-source
    effect: reads
    facts: &id001
    - Name
    - Last seen
    - Readings
    - Included
  - entity: source-settings
    effect: reads
    facts: &id002
    - Order
    - First choices
    - Totals
  actor: person
  contexts:
    personal:
      place: web::personal::devices
    public:
      place: web::public::devices
- text: The Product lists each device and app in the order tried, with its last reading, the readings it reports, and on how many of its days in the window it was the one used.
  kind: product
  entities:
  - entity: data-source
    effect: reads
    facts: *id001
  - entity: source-settings
    effect: reads
    facts: *id002
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

# See where each reading comes from

## Trigger

Devices and apps have reported readings.

## Outcome

The person can see which device each reading comes from, and that another came first on the days it was not used.
