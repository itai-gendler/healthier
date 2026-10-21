---
appliesTo:
- type: capability
  id: read-insights
- type: capability
  id: read-today
references:
- kind: code
  role: implementation
  target: src/pipeline/insights/place.ts#place
- kind: code
  role: implementation
  target: src/pipeline/insights/cards/floors.ts#pageFloor
---

# Each insight appears in one feed at a time

Today receives eligible findings while true or while news, according to each finding and the part of day. Otherwise a non-nudge finding remains on its subject page. A quiet Today may bring eligible page findings forward, cautious first, up to two. An empty subject feed points to its Today findings or uses an evidence-sensitive fallback.
