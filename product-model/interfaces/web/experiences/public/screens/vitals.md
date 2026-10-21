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

Vitals for the demo person: heart rate minute by minute and each overnight measure against the demo's usual range.
