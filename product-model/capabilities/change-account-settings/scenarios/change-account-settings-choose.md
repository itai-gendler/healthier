---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person chooses the theme preference.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::account
    public:
      place: web::public::account
- text: The Product saves the profile theme.
  kind: product
  entities:
  - entity: profile
    effect: changes
    facts:
    - Theme
  actor: person
  contexts:
    personal:
      place: web::personal::account
    public:
      place: web::public::account
references:
- kind: code
  role: implementation
  target: src/hooks/useTheme.tsx#ThemeProvider
- kind: code
  role: implementation
  target: src/views/DataCards.tsx#AccountCard
---

# Choose the preferred theme

## Trigger

The person changes the theme preference.

## Outcome

The theme applies immediately; a connected choice is saved and remembered for the next visit.

## Edge cases

- A failed connected save restores the earlier choice and shows a failure.
