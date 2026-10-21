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
    from: Reconnect required
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

# Reconnect an existing identity

## Trigger

The person returns through Google sign-in or is asked to reconnect.

## Outcome

Existing health history stays associated with the identity; renewed consent requests a full recent-window sync.

## Edge cases

- If Google omits ongoing access and none is already stored, consent is requested once more; failure after that is reported.
