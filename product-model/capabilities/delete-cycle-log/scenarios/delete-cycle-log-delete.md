---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person confirms deletion of the cycle log.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle-settings
    public:
      place: web::public::cycle-settings
- text: The Product removes cycle days and rejected starts and resets cycle settings.
  kind: product
  entities:
  - entity: cycle-day
    effect: removes
  - entity: rejected-start
    effect: removes
  - entity: cycle-settings
    effect: changes
    facts:
    - Tracking
    - Today cards
    - Other pages
    - Log kept
  - entity: health-day
    effect: changes
    facts:
    - Sleeping heart rate floor
  actor: person
  contexts:
    personal:
      place: web::personal::cycle-settings
    public:
      place: web::public::cycle-settings
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

# Delete cycle data

## Trigger

The person confirms Delete cycle data.

## Outcome

Logged days and rejected starts are removed, tracking is off, the other cycle preferences return to defaults, and sleeping heart rate floors are cleared.

## Edge cases

- Cancelling confirmation preserves the log.
