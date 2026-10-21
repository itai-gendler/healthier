---
appliesTo:
- type: entity
  id: health-day
- type: entity
  id: sleep-session
- type: capability
  id: read-sleep-breathing
- type: capability
  id: read-system-strain
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
  target: src/pipeline/derive.ts#values
- kind: code
  role: implementation
  target: src/pipeline/normalize.ts#emptyRecord
---

# An absent reading stays distinct from zero

No observation is unknown, not zero activity, zero sleep or proof of a quiet Lab. Summaries and comparisons use their recorded observations and state insufficient evidence.
