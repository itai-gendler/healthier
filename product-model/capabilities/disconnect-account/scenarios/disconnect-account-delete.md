---
kind: primary
routes:
  personal: Connected profile
steps:
- text: The person confirms deletion.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::account
- text: The Product revokes connected access and deletes the account and its data.
  kind: product
  entities:
  - entity: account
    effect: removes
  - entity: google-connection
    effect: removes
    with: account
    from: Connected
  - entity: profile
    effect: removes
  - entity: goals
    effect: removes
    with: profile
  - entity: cycle-settings
    effect: removes
    with: profile
  - entity: source-settings
    effect: removes
    with: profile
  - entity: synchronization
    effect: removes
    with: profile
    from: Ready
  - entity: health-day
    effect: removes
    with: profile
  - entity: sleep-session
    effect: removes
    with: profile
  - entity: heart-rate-day
    effect: removes
    with: profile
  - entity: data-source
    effect: removes
    with: profile
    from: 'On'
  - entity: data-stream
    effect: removes
    with: profile
    from: Current
  - entity: cycle-day
    effect: removes
    with: profile
  - entity: rejected-start
    effect: removes
    with: profile
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
  target: src/App.tsx#App
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
- kind: code
  role: implementation
  target: server/repo.ts#deleteUser
---

# Disconnect and delete stored data

## Trigger

The person confirms Disconnect & delete data.

## Outcome

The account, connected access and all stored personal health and cycle data are removed, and the welcome view opens.

## Edge cases

- Cancelling confirmation leaves the account intact.
