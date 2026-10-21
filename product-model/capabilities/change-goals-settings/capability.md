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
  target: src/hooks/useGoals.tsx#GoalsProvider
- kind: code
  role: implementation
  target: src/pipeline/goals.ts#parseGoals
domain: goals
---

# Change goals settings

Set daily steps, daily brisk minutes and nightly sleep need in the Goals section, or return sleep need to Auto.
