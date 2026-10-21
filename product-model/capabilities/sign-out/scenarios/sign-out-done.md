---
kind: primary
routes:
  personal: Connected profile
steps:
- text: The person chooses Sign out.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::account
- text: The Product ends the current session.
  kind: product
  entities:
  - entity: person
    effect: changes
    facts:
    - Signed in
  actor: person
  contexts:
    personal:
      place: web::personal::account
references:
- kind: code
  role: implementation
  target: src/hooks/useAuth.ts#useAuth
- kind: code
  role: implementation
  target: server/auth.ts#authRoutes
---

# Sign out while retaining data

## Trigger

The person chooses Sign out.

## Outcome

The session ends and the welcome view opens; stored data and background access remain.
