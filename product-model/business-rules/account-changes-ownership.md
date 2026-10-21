---
appliesTo:
- type: entity
  id: account
  effect: changes
references:
- kind: code
  role: implementation
  target: server/auth.ts#requireUser
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
- kind: code
  role: implementation
  target: server/sync.ts#startScheduler
- kind: code
  role: implementation
  target: src/App.tsx#App
permits:
- related:
  - verb: owns
    entity: person
  when:
  - entity: person
    fact: Signed in
    is: true
  - entity: person
    fact: Admitted
    is: true
---

# Only the person changes their account

The operation stays within the person’s own information through an admitted connected session.
