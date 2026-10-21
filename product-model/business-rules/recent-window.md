---
appliesTo:
- type: entity
  id: health-day
- type: capability
  id: read-insights
- type: capability
  id: read-body-battery
references:
- kind: code
  role: implementation
  target: src/ui/span.tsx#useSpan
- kind: code
  role: implementation
  target: server/sync.ts#loadDataset
---

# Current judgements use the recent window

The dashboard’s analysis window is 62 civil days ending on the person’s today. Longer selected history changes descriptive views and historical records, not current baselines or readiness.
