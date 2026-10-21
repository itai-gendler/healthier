---
entities:
- entity: data-source
  shows:
  - Name
  - Last seen
  - Readings
  - Included
  collects:
  - Included
- entity: source-settings
  shows: &id001
  - Order
  - First choices
  - Totals
  collects: *id001
references:
- kind: code
  role: implementation
  target: src/views/SourcesCard.tsx#SourcesCard
---

# Devices and sources

Devices and sources in Demo mode: the demo person's watch and scale, shown with nothing to choose.
