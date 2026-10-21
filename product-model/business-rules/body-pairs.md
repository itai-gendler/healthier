---
appliesTo:
- type: entity
  id: health-day
  facts:
  - Body
  - Sources
- type: capability
  id: browse-body
references:
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#compositionPairs
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#bodyComposition
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#weightTrend
---

# Body composition uses distinct nearby compatible readings

Each weight pairs at most once with an unused body-fat reading, preferring the same day and allowing one adjacent day. Pairs with two known different sources are excluded. Composition trends need four pairs over 28 days; weight trends need three readings over 21 days.
