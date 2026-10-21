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
- text: The Product shows the last two weeks’ nights against the usual range, with no run of three on one side up to the latest.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Vitals
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

# Read nights inside the usual range

## Trigger

At least ten baseline readings in the six weeks before the last fortnight and seven recent readings are available.

## Outcome

The Lab reports its observed quiet result with the amount of data examined; this is not an all-clear.
