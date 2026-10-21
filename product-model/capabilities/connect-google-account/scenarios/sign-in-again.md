---
kind: alternate
routes:
  public: Welcome
steps:
- text: The person completes Google sign-in again.
  kind: actor
  entities: []
  actor: person
  contexts:
    public:
      place: web::public::welcome
- text: The Product renews connected access and refreshes the identity information.
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Name
    - Email
    - Picture
  - entity: google-connection
    effect: changes
    facts:
    - Shared categories
    - Available
    from: Connected
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

# Sign in again

## Trigger

The person completes Google sign-in for an existing connected account.

## Outcome

The account’s identity information and granted categories are refreshed. Stored health history and personal choices remain associated with the account.
