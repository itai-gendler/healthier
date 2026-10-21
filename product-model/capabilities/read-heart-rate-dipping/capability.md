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
  target: src/pipeline/labs.ts#dipping
domain: labs
---

# Read the Nocturnal HR dipping Lab

Read the Lab that compares daytime and sleeping heart rate over the last 30 finished days: the median day-to-night drop, its band, and how many nights dropped less than 10%.
