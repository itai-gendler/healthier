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
  target: src/pipeline/labs.ts#sdbScreen
domain: labs
---

# Read the Sleep-disordered breathing patterns Lab

Read the Lab that watches breathing during sleep: each of the last 14 nights' oxygen, breathing rate and time awake against the person's usual range from the four weeks before, and how many nights had two of them off together.
