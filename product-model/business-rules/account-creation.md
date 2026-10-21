---
appliesTo:
- type: entity
  id: account
  effect: creates
references:
- kind: code
  role: implementation
  target: server/auth.ts#authRoutes
- kind: code
  role: implementation
  target: server/access.ts#isAllowed
permits:
- actors:
  - person
  when:
  - entity: person
    fact: Admitted
    is: true
---

# Only an admitted Google sign-in creates an account

The installation’s optional email or domain list decides admission through Google consent. The same policy is checked on subsequent authenticated requests.
