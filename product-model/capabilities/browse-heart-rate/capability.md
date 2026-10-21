---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/HeartRateCard.tsx#HeartRateCard
- kind: code
  role: implementation
  target: src/charts/heartRate.ts
domain: vitals
---

# Browse heart rate

Explore minute heart rate across the retained recent window, with summaries for the interval in view.
