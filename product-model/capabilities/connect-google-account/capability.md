---
availability:
- place: web::public
references:
- kind: code
  role: implementation
  target: server/auth.ts#authRoutes
- kind: code
  role: implementation
  target: src/hooks/useAuth.ts#useAuth
domain: account
---

# Connect Google Account

Sign in through Google, create the account on first use, and connect or renew access to shared health categories.
