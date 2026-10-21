---
entities:
- entity: sleep-session
  shows:
  - Date
  - Kind
  - Timing
  - Duration
  - Stages
  - Efficiency
  - Source
- entity: goals
  shows:
  - Sleep need
- entity: health-day
  shows:
  - Date
  - Vitals
  - Sources
references:
- kind: code
  role: implementation
  target: src/views/SleepView.tsx#SleepView
---

# Sleep

Sleep for the demo person: the latest night, its score and stages, naps, sleep debt, regularity and sleep over time.
