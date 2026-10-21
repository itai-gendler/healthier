---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#CycleView
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#summarizeCycles
- kind: code
  role: implementation
  target: src/pipeline/cyclePhases.ts#cycleShape
domain: cycle
---

# Browse cycles

Read the phase the person is likely in, the cycle day, the next period as a range, past cycles and the nightly measures behind them. Available while cycle tracking is on.
