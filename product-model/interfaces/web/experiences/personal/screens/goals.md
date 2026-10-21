---
entities:
- entity: goals
  shows: &id001
  - Steps
  - Brisk minutes
  - Sleep need
  collects: *id001
references:
- kind: code
  role: implementation
  target: src/views/DataCards.tsx#GoalsCard
---

# Goals

The Goals section of Settings: daily steps, daily brisk minutes and nightly sleep need, each within its bounds, with Reset to defaults.
