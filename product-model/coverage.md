---
scope: The browser dashboard, account lifecycle, health synchronization, source selection, insights, cycle log and six automatic Labs, at 74b02a122410b81b6aee92f2d2954abbde64fd2b.
method: Static inspection of the pinned tracked source, product documentation and selected tests.
covered:
- description: Browser orchestration, dashboard views and account-backed preferences.
  paths:
  - src/App.tsx
  - src/views/
  - src/components/
  - src/charts/
  - src/hooks/
  - src/ui/span.tsx
- description: Health synchronization, normalization, history, derived comparisons, cycles and insight selection.
  paths:
  - src/pipeline/
- description: Account admission, API handlers, synchronization scheduling and persistence.
  paths:
  - server/
  - server.ts
- description: Data-status classification, civil dates, theme and sign-in note helpers, and the health facts used in the views.
  paths:
  - src/lib/
  - src/types/
exclusions:
- description: Build, packaging and deployment tooling; these are contributor operations rather than dashboard behavior.
  paths:
  - package.json
  - docker-compose.yml
  - docker-compose.dev.yml
  - .github/
  - Dockerfile
- description: Visual assets and rendering primitives; layout and styling are outside product meaning.
  paths:
  - public/
  - src/index.css
  - src/theme.css
  - src/ui/
  - src/views/silhouettes.ts
  - src/views/cycleColours.ts
unmapped:
- description: Individual insight-card thresholds beyond representative scenarios and shared selection rules; omitted to keep the model reviewable.
  paths:
  - src/pipeline/insights/cards/
  - src/pipeline/insights/patterns.ts
  - src/pipeline/insights/association.ts
- description: Peripheral nutrition, ECG and additional wellbeing payload details beyond their presence in Data streams; not primary dashboard workflows.
  paths:
  - src/pipeline/registry.ts
- description: Translation contributor tooling and pseudolocale behavior; the served English locale is recorded in the product.
  paths:
  - src/i18n/
  - src/locales/
- description: Browser installation prompts and native browser gestures; deployment-specific peripheral behavior.
  paths:
  - public/manifest.webmanifest
  - index.html
limitations: []
---

# Coverage


