---
entities:
- entity: installation
  shows:
  - Demo offered
  - Sign-in note
  - Terms address
  - Privacy notice address
references:
- kind: code
  role: implementation
  target: src/App.tsx#App
- kind: code
  role: implementation
  target: src/views/SignInParts.tsx#SignInConsent
---

# Welcome

Where a person who is not signed in chooses Connect Google Account or Demo mode, and reads the installation's own sign-in note and any sign-in message. When the installation has terms or a privacy notice, the screen links them and says that connecting accepts them; how Healthier uses the data also links the privacy notice.
