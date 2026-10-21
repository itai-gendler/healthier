---
entities:
- entity: health-day
  shows:
  - Date
  - Movement
  - Sources
- entity: goals
  shows:
  - Steps
  - Brisk minutes
references:
- kind: code
  role: implementation
  target: src/views/ActivityView.tsx#ActivityView
---

# Activity

Steps and brisk minutes against the person's own goals and the WHO's 150 minutes a week, with energy, distance, intensity and weekly totals, from the recent window back to all stored history.
