---
relations:
- entity: google-connection
  verb: has
  cardinality: one-to-one
domain: account
references:
- kind: code
  role: implementation
  target: server/repo.ts#upsertUser
- kind: code
  role: implementation
  target: server/auth.ts#authRoutes
---

# Account

The Google identity associated with a person’s persistent Healthier data.

## Information kept

- **Name** — Name supplied by Google.
- **Email** — Google email address.
- **Picture** — Google profile picture.
- **Time zone** — Zone used to determine the person’s civil day.
