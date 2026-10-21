---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/SleepView.tsx#SleepView
- kind: code
  role: implementation
  target: src/pipeline/sleep.ts#scoreSleep
domain: sleep
---

# Read sleep score

Understand the latest main sleep’s duration, restoration and efficiency contributions.
