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

Last night's sleep and its score, stages and architecture, the last seven nights against the person's sleep need, naps, sleep debt, the sleep window and regularity, and sleep over longer spans.
