---
availability:
- place: web::personal
- place: web::public
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
domain: cycle-settings
---

# Delete cycle data

Delete the cycle log and its settings: every logged day, every found start the person said was not a period, and the tracking choices.
