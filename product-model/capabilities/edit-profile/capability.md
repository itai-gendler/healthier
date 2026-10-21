---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/views/BodyView.tsx#ProfileTile
- kind: code
  role: implementation
  target: src/App.tsx#App
- kind: code
  role: implementation
  target: server/api.ts#apiRoutes
domain: body
---

# Edit profile

Set or clear the gender choice on Body; age and height remain supplied by Google.
