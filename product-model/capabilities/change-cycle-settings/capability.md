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

# Change cycle settings

Choose whether to track cycles, show cycle cards on Today, and allow for cycles elsewhere.
