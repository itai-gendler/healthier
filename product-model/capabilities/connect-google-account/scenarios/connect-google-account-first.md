---
kind: primary
routes:
  public: Welcome
steps:
- text: The person chooses to connect and completes Google consent.
  kind: actor
  entities: []
  actor: person
  contexts:
    public:
      place: web::public::welcome
- text: The Product creates the account and its connected access.
  kind: product
  entities:
  - entity: account
    effect: creates
    facts:
    - Name
    - Email
    - Picture
    - Time zone
  - entity: google-connection
    effect: creates
    with: account
    facts:
    - Shared categories
    - Available
    to: Connected
  - entity: person
    effect: changes
    facts:
    - Signed in
    - Admitted
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

# Connect for the first time

## Trigger

The person chooses Connect Google Account.

## Outcome

The Google identity is signed in; Healthier requests a full import before presenting the first dashboard.
