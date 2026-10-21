---
appliesTo:
- type: entity
  id: rejected-start
  effect: creates
references:
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
- kind: code
  role: implementation
  target: server/sync.ts#syncUserLocked
- kind: code
  role: implementation
  target: src/hooks/useCycle.tsx#CycleProvider
permits:
- related: &id001
  - verb: keeps
    entity: profile
  - verb: uses
    entity: person
  when:
  - entity: person
    fact: Signed in
    is: true
  - entity: person
    fact: Admitted
    is: true
- related: *id001
  when:
  - entity: profile
    fact: Origin
    is: Demo
---

# Only the person creates their rejected start

The operation stays within the person’s own information through an admitted connected session. Their temporary demonstration information is also available in Demo mode.
