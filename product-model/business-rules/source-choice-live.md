---
appliesTo:
- type: entity
  id: source-settings
  effect: changes
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

# Only the connected person changes source preferences

The demonstration displays source choices; changing which individual sources count or which sources are preferred is offered on connected profiles.
