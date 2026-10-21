---
kind: alternate
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person changes the two presentation choices.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::cycle-settings
    public:
      place: web::public::cycle-settings
- text: The Product saves cycle settings.
  kind: product
  entities:
  - entity: cycle-settings
    effect: changes
    facts:
    - Today cards
    - Other pages
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

# Choose where cycle information contributes

## Trigger

Tracking is on and the person changes Today cards or Other pages.

## Outcome

Today placement and cycle-aware comparisons follow the choices; the Cycle page remains available.
