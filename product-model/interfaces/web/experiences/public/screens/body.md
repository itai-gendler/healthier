---
entities:
- entity: health-day
  shows:
  - Date
  - Body
  - Sources
- entity: profile
  shows:
  - Age
  - Height
  - Gender
  collects:
  - Gender
references:
- kind: code
  role: implementation
  target: src/views/BodyView.tsx#BodyView
---

# Body

Body for the demo person: weight and its trend, body fat, lean and fat mass, BMI and the gender choice.
