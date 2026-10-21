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

Labs: six experiments that look for multi-week patterns in the person's own data, each with what it watches, what it found and how it works.
