# AGENTS.md

Source of truth for AI agents: [`.github/copilot-instructions.md`](.github/copilot-instructions.md) and the scoped rules in
[`.github/instructions/`](.github/instructions/). Read them first.

## Definition of done
`pnpm typecheck && pnpm lint && pnpm test` must pass. Run `pnpm e2e` when routes or user flows change.

## Guardrails for autonomous changes
- Small, focused PRs; don't refactor unrelated code.
- Never modify: `src/app/**` (app-shell wiring), `src/api/generated/**`, `vite.config.ts`, `pnpm-lock.yaml` by hand, CI workflows.
- Never upgrade or add `@enterprise/*` packages or major dependencies — propose it in the PR description.
- Add/update tests for every behavior change; include an accessibility check for new UI.
- Include before/after screenshots in the PR for visual changes.
