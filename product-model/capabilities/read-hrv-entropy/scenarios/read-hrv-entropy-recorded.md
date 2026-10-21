---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens HRV entropy on Labs.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Vitals
  actor: person
  contexts:
    personal:
      place: web::personal::labs
    public:
      place: web::public::labs
- text: The Product reports a shift after at least three consecutive recorded nights outside the earlier range on the same side, including the latest reading.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
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
  target: src/pipeline/labs.ts#entropyShift
---

# Report a shift in HRV entropy

## Trigger

The person opens the Lab. At least ten baseline readings in the six weeks before the last fortnight and seven recent readings are available.

## Outcome

The card shows the last two weeks’ nights against the usual range and how many nights in a row have shifted.
