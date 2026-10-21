---
appliesTo:
- type: entity
  id: data-source
- type: entity
  id: source-settings
- type: entity
  id: health-day
references:
- kind: code
  role: implementation
  target: src/pipeline/sources.ts#sourceRanking
- kind: code
  role: implementation
  target: src/pipeline/sources.ts#sourceOrders
- kind: code
  role: implementation
  target: src/pipeline/incremental.ts#assembleDays
---

# The first available included source supplies each reading

A per-reading first choice precedes the person’s global order; unplaced sources follow by most recent report, then reported days. Each day takes the first included source with a reading. Choices apply across retained history when it is read.
