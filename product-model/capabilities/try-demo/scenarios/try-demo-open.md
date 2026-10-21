---
kind: primary
routes:
  public: Demo mode
steps:
- text: The person chooses Demo mode.
  kind: actor
  entities: []
  actor: person
  contexts:
    public:
      place: web::public::welcome
- text: The Product creates the temporary profile and its demonstration readings, then opens Today.
  kind: product
  entities:
  - entity: profile
    effect: creates
    facts:
    - Origin
    - Age
    - Height
    - Gender
    - Theme
  - entity: goals
    effect: creates
    with: profile
    facts:
    - Steps
    - Brisk minutes
    - Sleep need
  - entity: cycle-settings
    effect: creates
    with: profile
    facts:
    - Tracking
    - Today cards
    - Other pages
    - Log kept
  - entity: source-settings
    effect: creates
    with: profile
    facts:
    - Order
    - First choices
    - Totals
  - entity: synchronization
    effect: creates
    with: profile
    facts:
    - Progress
    - Last sync
    - Failure
    - Window
    - History
    to: Ready
  - entity: health-day
    effect: creates
    with: profile
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
    effect: creates
    with: profile
    facts:
    - Date
    - Kind
    - Timing
    - Duration
    - Stages
    - Efficiency
    - Source
  - entity: heart-rate-day
    effect: creates
    with: profile
    facts:
    - Date
    - Readings
  - entity: data-source
    effect: creates
    with: profile
    facts:
    - Name
    - Last seen
    - Readings
    - Included
    to: 'On'
  - entity: data-stream
    effect: creates
    with: profile
    facts:
    - Reading
    - Latest day
    - Coverage
    - Fetch detail
    - Shared
    to: Current
  - entity: cycle-day
    effect: creates
    with: profile
    facts:
    - Date
    - Flow
    - Symptoms
    - Note
  actor: person
  contexts:
    public:
      place: web::public::today
references:
- kind: code
  role: implementation
  target: src/App.tsx#App
- kind: code
  role: implementation
  target: src/hooks/useHealth.ts#demoResult
- kind: code
  role: implementation
  target: src/pipeline/demo.ts#DEMO_CLOCK
---

# Open the demonstration profile

## Trigger

The person chooses Demo mode.

## Outcome

Today opens with a deterministic demonstration profile, its full history and cycle example.
