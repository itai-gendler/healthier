---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Irregular rhythm notifications on Labs.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Notifications
  - entity: data-stream
    effect: reads
    facts: &id002
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
- text: The Product shows notification dates and counts exactly as supplied by the device; no notifications is distinct from a stream that has not synced.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
  - entity: data-stream
    effect: reads
    facts: *id002
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

# Show notifications as the device reported them

## Trigger

The device synced irregular rhythm notifications in the recent window.

## Outcome

Days with notifications are marked with their counts, and the card says Healthier does not analyse heart rhythm.
