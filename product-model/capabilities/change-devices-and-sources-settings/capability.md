---
availability:
- place: web::personal
references:
- kind: code
  role: implementation
  target: src/views/SourcesCard.tsx#SourcesCard
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
- kind: code
  role: implementation
  target: src/pipeline/sources.ts#sourceOrders
domain: devices-and-sources
---

# Change devices and sources settings

Set which device comes first, a first choice for a single reading, and which kinds of source count in daily totals. Offered for a connected account; Demo mode shows its sources with nothing to choose.
