---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/BodyView.tsx#BodyView
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#latestBody
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#bodyComposition
domain: body
---

# Browse Body

Read weight, body fat, lean and fat mass, BMI and sparse-measurement trends.
