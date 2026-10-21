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

Devices and sources: each device and app that reported readings, the days it reported and was used, which ones count, which comes first, and which kinds of source count in daily totals.
