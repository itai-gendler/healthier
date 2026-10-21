---
kind: primary
result: achieved
routes:
  connected: Connect and import
steps:
- text: The person chooses to connect and completes Google consent.
  kind: actor
  entities: []
  actor: person
  contexts:
    connected:
      place: web::public::welcome
  capability: connect-google-account
- text: The Product creates the account and its connected access.
  kind: product
  entities:
  - entity: account
    effect: creates
    facts:
    - Name
    - Email
    - Picture
    - Time zone
  - entity: google-connection
    effect: creates
    with: account
    facts:
    - Shared categories
    - Available
    to: Connected
  - entity: person
    effect: changes
    facts:
    - Signed in
    - Admitted
  actor: person
  contexts:
    connected:
      place: web::public::welcome
  capability: connect-google-account
- text: The person opens the connected dashboard.
  kind: actor
  entities: []
  actor: person
  contexts:
    connected:
      place: web::personal::today
  capability: sync-health-data
- text: The Product creates the connected profile and starts the recent-window import.
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
    to: Running
  actor: person
  contexts:
    connected:
      place: web::personal::today
  capability: sync-health-data
- text: The Product stores recorded days and available source descriptions.
  kind: product
  entities:
  - entity: health-day
    effect: creates
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
    facts:
    - Date
    - Readings
  - entity: data-stream
    effect: creates
    facts:
    - Reading
    - Latest day
    - Coverage
    - Fetch detail
    - Shared
    to: Current
  - entity: data-source
    effect: creates
    facts:
    - Name
    - Last seen
    - Readings
    - Included
    to: 'On'
  actor: person
  contexts:
    connected:
      place: web::personal::today
  capability: sync-health-data
- text: The Product finishes the window and presents Today.
  kind: product
  entities:
  - entity: synchronization
    effect: changes
    facts:
    - Progress
    - Last sync
    - Failure
    - Window
    - History
    from: Running
    to: Ready
  actor: person
  contexts:
    connected:
      place: web::personal::today
  capability: sync-health-data
- text: The person reads Today.
  kind: actor
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Movement
    - Vitals
    - Sources
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
  - entity: goals
    effect: reads
    facts:
    - Steps
    - Brisk minutes
    - Sleep need
  actor: person
  contexts:
    connected:
      place: web::personal::today
  capability: read-today
- text: The Product shows recent sleep and movement with their dates, current progress and overnight comparisons. Today’s movement remains in progress.
  kind: product
  entities:
  - entity: health-day
    effect: reads
    facts:
    - Date
    - Movement
    - Vitals
    - Sources
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
  - entity: goals
    effect: reads
    facts:
    - Steps
    - Brisk minutes
    - Sleep need
  actor: person
  contexts:
    connected:
      place: web::personal::today
  capability: read-today
references:
- kind: code
  role: implementation
  target: src/App.tsx#App
- kind: code
  role: implementation
  target: src/hooks/useHealth.ts#useHealth
---

# Reach Today after sign-in

## Trigger

The person connects Google Account at the welcome view.

## Outcome

The Product imports the recent window and presents Today.
