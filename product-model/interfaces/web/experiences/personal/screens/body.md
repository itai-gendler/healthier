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

Weight and its trend, body fat, lean and fat mass and BMI, with the age and height Google Health shares and the gender the person sets here.
