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
  target: src/pipeline/cycle.ts#cycleStarts
domain: cycle
---

# Confirm period start

Confirm a start found in the nightly data by recording the person’s own period entry. Available while cycle tracking is on.
