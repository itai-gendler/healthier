---
kind: alternate
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
- text: The Product says no notifications were synced, and that this does not mean the rhythm was checked.
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

# Show that none were synced

## Trigger

The stream is shared and synced, with no notifications in the recent window.

## Outcome

None synced is told apart from not synced; neither is an all-clear.
