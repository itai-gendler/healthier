---
appliesTo:
- type: capability
  id: read-insights
- type: capability
  id: read-sleep-breathing
- type: capability
  id: read-heart-rate-dipping
references:
- kind: code
  role: implementation
  target: src/pipeline/insights/cards/today.ts#labsReminders
---

# Sleep-breathing and dipping reminders recur while their patterns remain

Sleep-breathing and dipping patterns produce Today findings on entry and on the first two days of a month while present. Shared conflict and placement rules still choose the displayed feed.
