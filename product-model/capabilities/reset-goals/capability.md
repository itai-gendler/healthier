---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/DataCards.tsx#GoalsCard
- kind: code
  role: implementation
  target: src/pipeline/goals.ts#DEFAULT_GOALS
domain: goals
---

# Reset goals

Restore the default goals together with Reset to defaults: 10,000 steps, 30 brisk minutes and Auto sleep need.
