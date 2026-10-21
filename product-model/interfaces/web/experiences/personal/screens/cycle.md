---
entities:
- entity: cycle-day
  shows: &id001
  - Date
  - Flow
  - Symptoms
  - Note
  collects: *id001
- entity: health-day
  shows:
  - Date
  - Vitals
  - Sleeping heart rate floor
  - Sources
- entity: cycle-settings
  shows:
  - Tracking
  - Today cards
  - Other pages
  - Log kept
references:
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#CycleView
---

# Cycle

The phase the person is likely in and the day of their cycle, the next period as a range, past cycles, the nightly measures they were found in, and the log of periods and how the person felt. Offered while cycle tracking is on.
