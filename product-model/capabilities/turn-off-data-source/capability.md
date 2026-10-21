---
availability:
- place: web::personal
references:
- kind: code
  role: implementation
  target: src/views/SourcesCard.tsx#SourceRow
- kind: code
  role: implementation
  target: src/pipeline/sources.ts#sourceOrders
domain: devices-and-sources
---

# Turn off data source

Switch a device or app off so its readings are left out of the person's days and usual ranges. Its stored readings and its place in the order are kept.
