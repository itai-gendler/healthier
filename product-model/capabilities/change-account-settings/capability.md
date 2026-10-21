---
availability:
- place: web::personal
- place: web::public
references:
- kind: code
  role: implementation
  target: src/hooks/useTheme.tsx#ThemeProvider
- kind: code
  role: implementation
  target: src/views/DataCards.tsx#AccountCard
domain: account
---

# Change account settings

Choose a dark, light or Match device theme in the Account section. The choice is kept with a connected account, so it follows the person to every device; in Demo mode it lasts as long as the demo.
