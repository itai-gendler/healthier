---
kind: edge
routes:
  public: Welcome
steps:
- text: The person begins Google sign-in.
  kind: actor
  entities: []
  actor: person
  contexts:
    public:
      place: web::public::welcome
- text: The Product shows the sign-in failure without presenting a new dashboard.
  kind: product
  entities: []
  actor: person
  contexts:
    public:
      place: web::public::welcome
references:
- kind: code
  role: implementation
  target: server/auth.ts#authRoutes
- kind: code
  role: implementation
  target: src/hooks/useAuth.ts#useAuth
---

# Return from cancelled consent

## Trigger

Google consent is cancelled or the callback cannot complete.

## Outcome

The welcome view shows cancellation or the sign-in failure; the person can try again.
