---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Body.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::body
    public:
      place: web::public::body
- text: Without a weigh-in the Product says so and still shows age, height and the gender choice; BMI waits for both a weight and a height.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Body
    - Sources
  - entity: profile
    effect: reads
    facts:
    - Age
    - Height
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
  target: src/views/BodyView.tsx#BodyView
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#latestBody
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#bodyComposition
---

# Show Body before any weigh-in

## Trigger

No weight has been recorded.

## Outcome

Nothing is estimated in place of a missing weight or height.
