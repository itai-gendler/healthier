---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/VitalsView.tsx#VitalsView
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#compareToBaseline
domain: vitals
---

# Browse vitals

Read HRV, resting heart rate, breathing, oxygen, skin-temperature deviation and cardio fitness over time.
