---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Vitals and picks a span.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
    - Vitals
    - Sources
  actor: person
  contexts:
    personal:
      place: web::personal::vitals
    public:
      place: web::public::vitals
- text: The Product shows HRV, resting heart rate, breathing, blood oxygen, skin temperature and cardio fitness against the person's usual range; a longer span changes the trend charts, never the usual range.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
  actor: person
  contexts:
    personal:
      place: web::personal::vitals
    public:
      place: web::public::vitals
references:
- kind: code
  role: implementation
  target: src/views/VitalsView.tsx#VitalsView
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#compareToBaseline
---

# Read each overnight measure against its usual range

## Trigger

Resting heart rate has been recorded in the recent window.

## Outcome

Each measure says whether its latest reading is usual for this person, judged against their own previous 28 days.
