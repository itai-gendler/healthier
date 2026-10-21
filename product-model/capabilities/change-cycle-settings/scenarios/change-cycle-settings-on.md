---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person enables tracking.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle-settings
    public:
      place: web::public::cycle-settings
- text: The Product saves cycle settings and reads any kept log.
  kind: product
  entities:
  - entity: cycle-settings
    effect: changes
    facts:
    - Tracking
  - entity: cycle-day
    effect: reads
    facts:
    - Date
    - Flow
    - Symptoms
    - Note
  - entity: rejected-start
    effect: reads
    facts:
    - Date
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

# Turn on cycle tracking

## Trigger

The person turns tracking on.

## Outcome

The Cycle page and calculations become available; existing logged days are loaded. A connected profile starts a sync to compute sleeping heart rate floors.
