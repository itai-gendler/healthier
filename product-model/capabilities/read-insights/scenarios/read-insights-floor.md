---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Today when no card is due.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
- text: The Product shows a card for the part of the day that says only what is known, such as last night’s sleep and the body battery in the morning, or steps at midday.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Movement
    - Vitals
    - Body
    - Notifications
    - Zones
    - Sources
    - Sleeping heart rate floor
  - entity: sleep-session
    effect: reads
    facts:
    - Date
    - Kind
    - Timing
    - Duration
    - Stages
    - Efficiency
    - Source
  actor: person
  contexts:
    personal:
      place: web::personal::today
    public:
      place: web::public::today
references:
- kind: code
  role: implementation
  target: src/pipeline/insights/engine.ts#evaluate
- kind: code
  role: implementation
  target: src/pipeline/insights/conflicts.ts#settle
- kind: code
  role: implementation
  target: src/pipeline/insights/place.ts#place
---

# Say only what is known when nothing is due

## Trigger

No card is true or news for Today, and none can be brought forward.

## Outcome

The fallback card describes only the readings that exist; missing data never becomes a claim that everything is steady.
