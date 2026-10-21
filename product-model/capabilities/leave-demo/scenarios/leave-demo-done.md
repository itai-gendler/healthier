---
kind: primary
routes:
  public: Demo mode
steps:
- text: The person chooses Exit demo.
  kind: actor
  entities: []
  actor: person
  contexts:
    public:
      place: web::public::account
- text: The Product removes the temporary profile and its data.
  kind: product
  entities:
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
  actor: person
  contexts:
    public:
      place: web::public::account
references:
- kind: code
  role: implementation
  target: src/App.tsx#App
---

# Exit the demo

## Trigger

The person chooses Exit demo in the Account section.

## Outcome

The demonstration ends and its temporary choices are discarded.
