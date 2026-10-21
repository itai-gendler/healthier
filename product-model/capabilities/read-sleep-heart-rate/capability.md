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
  target: src/pipeline/labs.ts#nocturnalTachycardia
domain: labs
---

# Read the Nocturnal tachycardia Lab

Read the Lab that looks for fast heart rate during sleep: stretches of recorded sleep above 100 bpm for ten minutes or more, with their time, length, peak and sleep stage.
