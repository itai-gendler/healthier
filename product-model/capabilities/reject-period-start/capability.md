---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#CycleHero
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#withRejected
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#cycleStarts
domain: cycle
---

# Reject period start

Mark a found start as not a period. Available while cycle tracking is on.
