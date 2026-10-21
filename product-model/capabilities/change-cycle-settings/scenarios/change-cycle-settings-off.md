---
kind: alternate
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person turns tracking off.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle-settings
    public:
      place: web::public::cycle-settings
- text: The Product saves cycle settings and clears the cycle-only derived readings.
  kind: product
  entities:
  - entity: cycle-settings
    effect: changes
    facts:
    - Tracking
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

# Turn off cycle tracking

## Trigger

The person turns tracking off.

## Outcome

Cycle calculations stop, the Cycle page is no longer offered, the log stays kept, and derived sleeping heart rate floors are removed.
