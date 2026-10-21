---
kind: validation
routes:
  public: Welcome
steps:
- text: The person signs in through Google and completes consent.
  kind: actor
  entities: []
  actor: person
  contexts:
    public:
      place: web::public::welcome
- text: The Product finds the verified Google email outside the addresses and domains the installation admits, and hands back the access Google just granted.
  kind: product
  entities:
  - entity: installation
    effect: reads
    facts:
    - Allowed emails
  actor: person
  contexts:
    public:
      place: web::public::welcome
- text: The Product explains that only invited people can join here and that the person should ask whoever runs it to add them.
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
  target: server/access.ts#isAllowed
---

# Turn away an account the installation does not admit

## Trigger

The installation lists the email addresses or domains that may join, and the person signs in with a Google account that is not on the list.

## Outcome

No account is created and nothing is stored; the sign-in screen explains that the installation is invite-only.
