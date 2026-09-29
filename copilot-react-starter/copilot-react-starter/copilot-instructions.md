# Copilot Instructions — <AppName>

> Always-on context. Keep under ~150 lines. Folder/file-type rules live in `.github/instructions/`.

## What this app is
- <One sentence: e.g. "Customer self-service portal for the Retail domain.">
- Owner: <team> · ARB reference: <ARB-ID> · Built on the Enterprise UI Accelerators reference architecture: <link>

## Tech stack
- React 19 + TypeScript (strict), Vite, pnpm workspaces
- Scaffolding/baseline: `create-enterprise-app` → `@enterprise/app-shell` (layout, routing, auth, error boundaries, telemetry)
- Design system: `@enterprise/ui` (components + design tokens). Styling via tokens/CSS Modules — no ad-hoc CSS frameworks.
- Routing: TanStack Router (file-based, type-safe)
- Server state: TanStack Query with the generated OpenAPI client in `src/api/generated`
- Client state: Zustand (only for true UI/global state)
- Forms: React Hook Form + Zod
- Auth: `@enterprise/auth` (OIDC/PKCE); i18n: `@enterprise/i18n` (i18next)
- Tests: Vitest + React Testing Library + MSW; E2E: Playwright

## Project layout
```
src/
  app/            # providers, router, app-level config (owned by app-shell — change rarely)
  routes/         # file-based routes; route components stay thin
  features/<name>/
    components/   # feature-specific components
    hooks/        # useXxx hooks (queries, mutations, logic)
    api/          # query keys + query/mutation hooks wrapping the generated client
    schemas/      # Zod schemas
    index.ts      # public surface of the feature — import only from here
  shared/         # cross-feature utilities & components not in @enterprise/ui
  api/generated/  # OpenAPI client — NEVER edit by hand
e2e/              # Playwright specs
```
Features must not import from another feature's internals — only via its `index.ts`.

## Commands
- Install: `pnpm install` · Dev: `pnpm dev`
- Typecheck: `pnpm typecheck` · Lint: `pnpm lint` · Unit tests: `pnpm test`
- E2E: `pnpm e2e` · Regenerate API client: `pnpm api:generate`

## Non-negotiables
- Use `@enterprise/ui` components first. Do not build a new Button/Modal/Table/etc. or add another UI library.
- No hard-coded colors, spacing, or fonts — use design tokens.
- All server data goes through TanStack Query hooks; no `fetch`/`axios` in components, no server data in Zustand.
- No tokens/secrets in code, `localStorage`, or logs. Auth only via `@enterprise/auth` hooks.
- Never use `dangerouslySetInnerHTML` (unless sanitized with the approved sanitizer and reviewed).
- WCAG 2.2 AA is required: semantic HTML, labels, keyboard support, focus management.
- All user-facing text through `t('...')` — no hard-coded strings.
- TypeScript strict: no `any`, no `@ts-ignore` (use `@ts-expect-error` with a reason if unavoidable).
- New npm dependencies must be listed in the PR description (ARB approved-list check).

## Key decisions (see /docs/adr)
- ADR-UI-001: TanStack Query for server state; Zustand only for client state.
- ADR-UI-002: Feature-sliced folder structure with public `index.ts`.
- ADR-UI-004: Micro-frontends are opt-in only with ARB approval.

## When unsure
Mirror an existing feature in `src/features/`. Ask rather than invent a new pattern.
