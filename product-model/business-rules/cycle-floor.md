---
appliesTo:
- type: entity
  id: health-day
  facts:
  - Sleeping heart rate floor
- type: entity
  id: cycle-settings
references:
- kind: code
  role: implementation
  target: server/sync.ts#deriveSleepHrFloor
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
- kind: code
  role: implementation
  target: src/pipeline/sleepHrFloor.ts
---

# Sleeping heart rate floor is kept only for cycle tracking

Tracking starts computation of the main sleep’s tenth-percentile minute heart rate with at least 120 recorded minutes and at least half its minutes recorded, and backfills older nights. Turning tracking off or deleting the log clears this derived stream. The finder uses non-REM heart rate until floors are available.
