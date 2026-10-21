---
kind: primary
routes:
  personal: Connected profile
  public: Demo mode
steps:
- text: The person opens Nocturnal tachycardia on Labs.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts: &id001
    - Date
  - entity: sleep-session
    effect: reads
    facts: &id002
    - Date
    - Kind
    - Timing
    - Duration
    - Stages
    - Efficiency
    - Source
  - entity: heart-rate-day
    effect: reads
    facts: &id003
    - Date
    - Readings
  actor: person
  contexts:
    personal:
      place: web::personal::labs
    public:
      place: web::public::labs
- text: The Product shows stretches above 100 bpm with at least ten qualifying readings, their time, duration, peak and available sleep stage; awake segments and gaps over two minutes break a stretch.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts: *id001
  - entity: sleep-session
    effect: reads
    facts: *id002
  - entity: heart-rate-day
    effect: reads
    facts: *id003
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
  target: src/pipeline/labs.ts#nocturnalTachycardia
---

# Find stretches of fast heart rate during sleep

## Trigger

The person opens the Lab. At least one sleep date has a session with minute readings covering half of its duration.

## Outcome

Each stretch shows with its night or nap, time, length, peak and sleep stage. Every day from the first scanned to the latest is drawn at the highest heart rate held for ten minutes while asleep, against the 100 bpm line; the days with a stretch sit above it.
