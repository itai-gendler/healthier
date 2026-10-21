---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Body.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Body
    - Sources
  - entity: profile
    effect: reads
    facts: &id002
    - Age
    - Height
    - Gender
  actor: person
  contexts:
    personal:
      place: web::personal::body
    public:
      place: web::public::body
- text: The Product shows the latest weigh-in and its date whatever span is chosen, the change since the one before, the weight trend, and body fat, lean and fat mass from weigh-ins paired with a body-fat reading.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
  - entity: profile
    effect: reads
    facts: *id002
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

# Read weight and body composition

## Trigger

The person opens Body with weigh-ins recorded.

## Outcome

Body shows the newest known weight and its trend, with body composition only from suitable weight and body-fat pairs.
