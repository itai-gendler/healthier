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

The Cycle page for the demo person, whose made-up cycles and logged periods show how phases, found starts and the log work together.
