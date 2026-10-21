---
appliesTo:
- type: entity
  id: sleep-session
- type: capability
  id: read-sleep-score
references:
- kind: code
  role: implementation
  target: src/pipeline/sleep.ts#scoreSleep
---

# Sleep score exposes duration restoration and efficiency

The score combines up to 50 duration points, 25 restoration points and 25 efficiency points, bounded to 1–100. Duration gives full points at 7–9 hours. Missing stages leave restorative percentage unknown and use 13 restoration points.
