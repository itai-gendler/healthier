---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/BodyBattery.tsx
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#readiness
domain: today
---

# Read body battery

Understand the readiness score, confidence, missing signals and signed contributions from the person’s readings.
