---
appliesTo:
- type: capability
  id: read-insights
- type: capability
  id: browse-cycles
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
- kind: doc
  role: intent
  target: README.md
- kind: doc
  role: intent
  target: CONTRIBUTING.md
- kind: code
  role: implementation
  target: src/views/LabsView.tsx
---

# Healthier findings describe wellness observations

Scores and Labs describe readings and their comparisons. They do not diagnose, screen for, rule out or treat a medical condition. Cycle phases are estimates, including inferred ovulation, and cannot establish fertility.
