---
entities:
- entity: health-day
  shows:
  - Date
  - Vitals
  - Zones
  - Sources
- entity: heart-rate-day
  shows:
  - Date
  - Readings
references:
- kind: code
  role: implementation
  target: src/views/VitalsView.tsx#VitalsView
---

# Vitals

Heart rate minute by minute with the person's zones, and HRV, resting heart rate, breathing, blood oxygen, skin temperature and cardio fitness, each against the person's usual range.
