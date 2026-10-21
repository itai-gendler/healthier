---
kind: alternate
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person chooses Back to auto.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::goals
    public:
      place: web::public::goals
- text: The Product clears the explicit sleep need in goals.
  kind: product
  entities:
  - entity: goals
    effect: changes
    facts:
    - Sleep need
  actor: person
  contexts:
    personal:
      place: web::personal::goals
    public:
      place: web::public::goals
references:
- kind: code
  role: implementation
  target: src/views/DataCards.tsx#GoalsCard
- kind: code
  role: implementation
  target: src/hooks/useGoals.tsx#GoalsProvider
- kind: code
  role: implementation
  target: src/pipeline/goals.ts#parseGoals
---

# Return sleep need to Auto

## Trigger

The person chooses Back to auto for sleep need.

## Outcome

The median recorded night, held between 7 and 8.5 hours, becomes the common sleep need; with no nights the fallback is 7.5 hours.
