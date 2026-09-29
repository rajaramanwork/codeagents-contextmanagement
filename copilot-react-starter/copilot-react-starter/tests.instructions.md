---
applyTo: "src/**/*.test.ts,src/**/*.test.tsx,e2e/**"
description: "Testing conventions — Vitest, React Testing Library, MSW, Playwright, axe"
---
# Testing conventions

## Unit / component (Vitest + React Testing Library)
- Co-locate tests: `OrderSummary.test.tsx` next to `OrderSummary.tsx`.
- Render with `renderWithProviders()` from `src/test/utils` (QueryClient, router, i18n, theme).
- Query by role/label/text as a user would (`getByRole('button', { name: /cancel/i })`); `data-testid` is a last resort.
- Interact with `userEvent`, not `fireEvent`. Await async UI with `findBy*`.
- Test behavior, not implementation — no assertions on hook internals, state, or class names.
- Mock the network with MSW handlers in `src/test/msw/handlers`; never mock TanStack Query or the generated client.
- Include an `axe` accessibility assertion for every new component: `expect(await axe(container)).toHaveNoViolations()`.
- Cover: loading, success, empty, error, and permission-denied states.

## E2E (Playwright)
- One spec per user journey in `e2e/<journey>.spec.ts`; use the Page Object helpers in `e2e/pages`.
- Use role-based locators; no fixed `waitForTimeout`.
- Authenticate via the stored auth state fixture — never type real credentials.
- Run against mocked or ephemeral backends; no production data.
