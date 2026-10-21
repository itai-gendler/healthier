---
appliesTo:
- type: entity
  id: cycle-day
- type: entity
  id: rejected-start
references:
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#loggedPeriods
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#cycleStarts
---

# Logged period starts take precedence over found starts

Spotting does not start or extend a period. Bleeding days separated by one missing day form one logged period; a single bleeding day establishes a start without a known duration. Logged starts override nearby found starts; rejections exclude found starts within two days.
