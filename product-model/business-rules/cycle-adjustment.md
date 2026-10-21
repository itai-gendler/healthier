---
appliesTo:
- type: entity
  id: cycle-settings
- type: capability
  id: read-insights
- type: capability
  id: read-system-strain
references:
- kind: code
  role: implementation
  target: src/hooks/useCycle.tsx#CycleProvider
- kind: code
  role: implementation
  target: src/pipeline/insights/engine.ts#cycleAware
- kind: code
  role: implementation
  target: src/pipeline/labs.ts#strainToday
---

# Cycle awareness can explain a deviation but cannot create an alarm

While Tracking and Other pages are on, three cycles can establish typical shifts for judging other pages. Cycle-sensitive findings must survive the adjusted comparison. Displayed measurements and body battery stay based on original readings.
