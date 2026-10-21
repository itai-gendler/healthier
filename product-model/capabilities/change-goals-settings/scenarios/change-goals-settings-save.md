---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person changes the target values.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::goals
    public:
      place: web::public::goals
- text: The Product saves the goals.
  kind: product
  entities:
  - entity: goals
    effect: changes
    facts:
    - Steps
    - Brisk minutes
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

# Set personal goals

## Trigger

The person adjusts a target.

## Outcome

The choices apply across progress, comparisons and insights; connected choices are saved, while demo choices last for the demo.
