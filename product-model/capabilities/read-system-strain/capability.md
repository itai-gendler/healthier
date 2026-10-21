---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/LabsView.tsx#LabsView
- kind: code
  role: implementation
  target: src/pipeline/labs.ts#strainToday
domain: labs
---

# Read the System Strain Radar Lab

Read the Lab that counts how many of today's resting heart rate, breathing rate, HRV and skin temperature are outside the person's usual range, from Baseline through Elevated to High.
