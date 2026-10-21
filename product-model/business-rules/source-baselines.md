---
appliesTo:
- type: entity
  id: health-day
- type: capability
  id: read-body-battery
references:
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#compareToBaseline
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#sameDevice
---

# A fill is judged against its own source history

A reading filled by another source is labelled as such and compared with that source’s prior readings. Ordinary usual-range comparisons require at least eight prior readings in the preceding 28 days; the latest reading is excluded from its own baseline.
