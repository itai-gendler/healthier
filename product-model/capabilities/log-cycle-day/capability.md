---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#DaySheet
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#StartSheetFor
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#withDay
domain: cycle
---

# Log cycle day

Record a dated flow, symptoms or note, including the My period started shortcut. Available while cycle tracking is on.
