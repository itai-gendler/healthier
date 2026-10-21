---
kind: edge
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens the Lab.
  kind: actor
  entities: []
  actor: person
  contexts:
    personal:
      place: web::personal::labs
    public:
      place: web::public::labs
- text: The Product says not synced when there are no stored notifications and the stream is unshared or failed.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Notifications
  - entity: data-stream
    effect: reads
    facts:
    - Reading
    - Latest day
    - Coverage
    - Fetch detail
    - Shared
  actor: person
  contexts:
    personal:
      place: web::personal::labs
    public:
      place: web::public::labs
references:
- kind: code
  role: implementation
  target: src/views/LabsView.tsx#LabsView
- kind: code
  role: implementation
  target: src/views/LabsView.tsx#irnLab
---

# Say the notifications are not synced

## Trigger

Irregular rhythm notifications were not shared with Healthier, or the last sync could not read them.

## Outcome

The card says Not synced instead of None synced.
