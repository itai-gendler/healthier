---
appliesTo:
- type: entity
  id: rejected-start
  effect: removes
  contexts:
  - place: web::personal::cycle
  - place: web::public::cycle
permits:
- when:
  - entity: cycle-settings
    fact: Tracking
    is: true
  related:
  - verb: keeps
    entity: profile
  - verb: uses
    entity: person
references:
- kind: code
  role: implementation
  target: src/App.tsx#PageNav
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#CycleView
---

# A rejected start is removed on the Cycle page only while tracking is on

The Cycle page and its log are offered only while cycle tracking is on; the ownership rules apply as well.
