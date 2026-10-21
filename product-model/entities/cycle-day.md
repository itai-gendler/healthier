---
domain: cycle
references:
- kind: code
  role: implementation
  target: src/pipeline/cycle.ts#CycleDay
- kind: code
  role: implementation
  target: src/views/CycleView.tsx#DaySheet
---

# Cycle day

A dated entry the person logs about bleeding, symptoms or a note.

## Information kept

- **Date** — The selected civil day.
- **Flow** — Spotting, light, medium, heavy, unspecified start, or no bleeding recorded.
- **Symptoms** — Selected symptoms from the supported list.
- **Note** — Optional trimmed note of up to 500 characters.
