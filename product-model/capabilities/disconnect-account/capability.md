---
availability:
- place: web::personal
references:
- kind: code
  role: implementation
  target: src/App.tsx#App
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
- kind: code
  role: implementation
  target: server/repo.ts#deleteUser
domain: account
---

# Disconnect and delete

End Healthier's access to the person's Google account and delete everything it stored for them: their days, goals, device choices, theme and cycle log. Their data in Google Health is not touched.
