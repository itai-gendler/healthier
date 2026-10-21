---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Cycle.
  kind: actor
  entities:
  - entity: cycle-day
    effect: reads
    facts: &id001
    - Date
    - Flow
    - Symptoms
    - Note
  - entity: health-day
    effect: reads
    facts: &id002
    - Date
    - Vitals
    - Sleeping heart rate floor
    - Sources
  - entity: cycle-settings
    effect: reads
    facts: &id003
    - Tracking
    - Today cards
    - Other pages
    - Log kept
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
- text: The Product leads with the likely phase and the cycle day, tells logged starts from found ones with how sure each is, and gives the next period as an early guess after two cycles or a range after three.
  kind: product
  entities:
  - entity: cycle-day
    effect: reads
    facts: *id001
  - entity: health-day
    effect: reads
    facts: *id002
  - entity: cycle-settings
    effect: reads
    facts: *id003
  actor: person
  contexts:
    personal:
      place: web::personal::cycle
    public:
      place: web::public::cycle
references:
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#CycleView
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#summarizeCycles
- kind: code
  role: implementation
  target: src/pipeline/cyclePhases.ts#cycleShape
---

# Read the current phase and the next period

## Trigger

Cycle tracking is on and the nights or the log show cycles.

## Outcome

A logged start reads as an exact day; a found one reads as about a day, give or take, with a likely tag. Phases are estimates.
