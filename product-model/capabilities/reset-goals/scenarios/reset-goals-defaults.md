---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person chooses Reset.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::goals
    public:
      place: web::public::goals
- text: The Product restores the default goals.
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
  target: src/pipeline/goals.ts#DEFAULT_GOALS
---

# Reset all goals

## Trigger

The person chooses Reset to defaults.

## Outcome

Goals return to 10,000 steps, 30 brisk minutes and Auto sleep need.
