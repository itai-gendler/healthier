---
kind: validation
routes:
  personal: Connected profile
steps:
- text: The person attempts to submit invalid targets.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::goals
- text: The Product keeps the saved goals.
  kind: product
  entities:
  - entity: goals
    effect: reads
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

# Reject an invalid target

## Trigger

A target is off its supported increments or outside its bounds.

## Outcome

The invalid values are not accepted.
