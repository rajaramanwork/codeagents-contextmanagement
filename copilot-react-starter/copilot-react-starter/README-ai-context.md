# AI Context Starter Kit — GitHub Copilot (React)

| Priority | File | Loaded | Purpose |
|---|---|---|---|
| 1 — Must | `.github/copilot-instructions.md` | Always | Stack, layout, commands, non-negotiables |
| 2 — Must | `.github/instructions/react-components.instructions.md` | `src/**/*.tsx` | Component structure, hooks, a11y, i18n |
| 3 — Must | `.github/instructions/design-system.instructions.md` | `*.tsx`, `*.module.css` | `@enterprise/ui` + design tokens |
| 4 — Must | `.github/instructions/data-state.instructions.md` | feature `api/`, `hooks/`, `schemas/`, stores | TanStack Query, Zustand, forms, API client |
| 5 — Must | `.github/instructions/tests.instructions.md` | tests, `e2e/**` | Vitest/RTL/MSW/axe, Playwright |
| 6 — Should | `AGENTS.md` | Coding agent / CLI | Pointer + agent guardrails |
| 7 — Should | `.github/prompts/new-feature.prompt.md` | `/new-feature` | Scaffold a feature slice |
| 8 — Nice | `.github/prompts/code-review.prompt.md` | `/code-review` | Standards-based UI review |
| 9 — Nice | `.github/agents/ui-arb-reviewer.agent.md` | Select agent | Read-only ARB compliance review |

## Adopting
1. Ideally ship these via `create-enterprise-app` so every new app starts with them.
2. Replace `<placeholders>`, package names (`@enterprise/*`), and ADR IDs with your real ones.
3. Swap stack choices you don't use (e.g. React Router instead of TanStack Router) — stale rules are worse than none.
4. Verify frontmatter keys against your Copilot/VS Code version (prompt-file `agent:` was formerly `mode:`).
5. Own these files via CODEOWNERS (Arche UI team) and review changes like code.
