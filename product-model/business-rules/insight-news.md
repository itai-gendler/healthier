---
appliesTo:
- type: capability
  id: read-insights
- type: capability
  id: read-today
references:
- kind: code
  role: implementation
  target: src/pipeline/insights/engine.ts#evaluate
- kind: code
  role: implementation
  target: src/pipeline/insights/context.ts#buildContext
- kind: code
  role: implementation
  target: server/sync.ts#answerHistory
---

# Insight novelty is derived from data rather than remembered visits

The same rules are evaluated on earlier cut-back windows to determine new findings. The data’s last day determines today; the clock selects part of day. Historical answers end before the recent window so current-window records can be judged as new.
