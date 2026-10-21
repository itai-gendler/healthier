---
appliesTo:
- type: capability
  id: read-sleep-breathing
- type: capability
  id: read-system-strain
- type: capability
  id: read-rhythm-notifications
- type: capability
  id: read-heart-rate-dipping
- type: capability
  id: read-hrv-entropy
- type: capability
  id: read-sleep-heart-rate
references:
- kind: code
  role: implementation
  target: src/pipeline/labs.ts
- kind: code
  role: implementation
  target: src/views/LabsView.tsx#LabsView
---

# Labs report only the evidence they examined

Each Lab is worked out again from the recorded data whenever it is read, and says whether it is collecting, waiting, quiet or has found a pattern. Too few nights reads as collecting, never as nothing found, and a quiet result is not an all-clear.
