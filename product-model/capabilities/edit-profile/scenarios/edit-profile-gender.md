---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person chooses female, male, other, or no selection.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::body
    public:
      place: web::public::body
- text: The Product saves the profile choice.
  kind: product
  entities:
  - entity: profile
    effect: changes
    facts:
    - Gender
  actor: person
  contexts:
    personal:
      place: web::personal::body
    public:
      place: web::public::body
references:
- kind: code
  role: implementation
  target: src/views/BodyView.tsx#ProfileTile
- kind: code
  role: implementation
  target: src/App.tsx#App
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
---

# Set the profile choice

## Trigger

The person changes the gender choice.

## Outcome

The choice is saved for a connected profile or held for the demo; Today reflects the change.

## Edge cases

- A failed save restores the previous value.
- An unsupported value is rejected without saving.
