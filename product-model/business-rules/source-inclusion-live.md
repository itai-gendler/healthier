---
appliesTo:
- type: entity
  id: data-source
  effect: changes
  facts:
  - Included
references:
- kind: code
  role: implementation
  target: src/views/SourcesCard.tsx#useSources
permits:
- related:
  - verb: keeps
    entity: profile
  - verb: uses
    entity: person
  when:
  - entity: profile
    fact: Origin
    is: Connected
  - entity: person
    fact: Signed in
    is: true
  - entity: person
    fact: Admitted
    is: true
---

# Only the connected person changes source inclusion

The person switches individual sources on or off for their own connected profile.
