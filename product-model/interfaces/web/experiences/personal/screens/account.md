---
entities:
- entity: account
  shows:
  - Name
  - Email
  - Picture
- entity: profile
  shows:
  - Theme
  collects:
  - Theme
references:
- kind: code
  role: implementation
  target: src/views/DataCards.tsx#AccountCard
---

# Account

The Account section of Settings: the Google account that is connected, the theme, Sign out, and Disconnect and delete.
