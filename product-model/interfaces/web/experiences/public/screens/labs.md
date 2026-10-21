---
entities:
- entity: health-day
  shows:
  - Date
  - Vitals
  - Notifications
  - Sources
- entity: sleep-session
  shows:
  - Date
  - Kind
  - Timing
  - Duration
  - Stages
  - Efficiency
  - Source
- entity: heart-rate-day
  shows:
  - Date
  - Readings
- entity: data-stream
  shows:
  - Reading
  - Latest day
  - Coverage
  - Fetch detail
  - Shared
references:
- kind: code
  role: implementation
  target: src/views/LabsView.tsx#LabsView
---

# Labs

Labs for the demo person, with something to show on every experiment.
