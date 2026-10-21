---
kind: edge
routes:
  personal: Connected profile
steps:
- text: The person confirms disconnection.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::account
- text: The Product reports that deletion could not complete.
  kind: product
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::account
references:
- kind: code
  role: implementation
  target: src/App.tsx#App
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
- kind: code
  role: implementation
  target: server/repo.ts#deleteUser
---

# Report a deletion failure

## Trigger

The deletion request fails.

## Outcome

The person receives a failure message and can retry.
