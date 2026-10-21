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

The Goals section of Settings in Demo mode; changes last only as long as the demo.
