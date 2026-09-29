---
agent: "agent"
description: "Scaffold a new feature slice (route, components, query hooks, schema, tests)"
argument-hint: "Feature and screen, e.g. 'Order history list with filters'"
---
Create a new feature for: **${input:feature:Feature and screen, e.g. Order history list with filters}**

Follow [copilot-instructions](../copilot-instructions.md) and the rules in
[components](../instructions/react-components.instructions.md), [design system](../instructions/design-system.instructions.md),
[data & state](../instructions/data-state.instructions.md), and [tests](../instructions/tests.instructions.md).

Steps:
1. Inspect an existing folder in `src/features/` and mirror its structure.
2. If new endpoints are needed, confirm they exist in `src/api/generated`; if not, stop and list what the backend must add.
3. `api/`: query-key factory, `queryOptions`, and query/mutation hooks.
4. `schemas/`: Zod schemas for any form or external input.
5. `components/`: presentational components using `@enterprise/ui`, tokens, `t()` strings, and full a11y.
6. `routes/`: a thin route file with typed search params for filters/pagination and a loader that prefetches.
7. Add i18n keys to `locales/en/<feature>.json`.
8. Tests: component tests (with MSW + axe) for loading/success/empty/error states; one Playwright journey.
9. Run `pnpm typecheck && pnpm lint && pnpm test`, fix failures, then summarize files changed and any new deps.
