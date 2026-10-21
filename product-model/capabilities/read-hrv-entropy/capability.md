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
  target: src/pipeline/labs.ts#entropyShift
domain: labs
---

# Read the HRV entropy Lab

Read the Lab that holds the device's nightly HRV entropy against the person's usual range from the six weeks before the last two, and reports a shift when several nights in a row leave it on the same side.
