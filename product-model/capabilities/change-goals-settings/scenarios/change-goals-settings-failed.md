---
kind: edge
routes:
  personal: Connected profile
steps:
- text: The person changes a target.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::goals
- text: The Product restores the saved goals.
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

# Restore saved goals

## Trigger

Saving the new targets fails.

## Outcome

The last saved targets return and the Goals section reports failure.
