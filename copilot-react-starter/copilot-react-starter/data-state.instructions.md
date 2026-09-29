---
applyTo: "src/features/**/api/**,src/features/**/hooks/**,src/features/**/schemas/**,src/**/*.store.ts"
description: "Server state, client state, forms/validation, and API client rules"
---
# Data, state & forms

## Server state — TanStack Query
- Wrap the generated client (`src/api/generated`) in feature hooks: `useOrderQuery`, `useCancelOrderMutation`.
- Query keys come from a per-feature factory — never inline arrays:
  ```ts
  export const orderKeys = {
    all: ['orders'] as const,
    list: (filters: OrderFilters) => [...orderKeys.all, 'list', filters] as const,
    detail: (id: string) => [...orderKeys.all, 'detail', id] as const,
  };
  ```
- Use `queryOptions()` helpers so the same options serve hooks, route loaders, and prefetching.
- Mutations invalidate or update the precise keys they affect; use optimistic updates only with rollback in `onError`.
- Don't set `staleTime: 0`/`Infinity` ad hoc — use the app-shell defaults unless there's a documented reason.
- Errors surface through the app-shell error boundary/toast; don't swallow errors in hooks.

## Client state — Zustand
- Only for cross-component UI state (e.g. sidebar, wizard step, selected rows). Never cache server data here.
- One store per concern in `*.store.ts`; select narrow slices (`useStore(s => s.x)`) to avoid re-renders.
- Prefer URL search params (typed via the router) for filters, sorting, and pagination — they're shareable.

## Forms & validation
- React Hook Form + `zodResolver`. Schemas in `schemas/`, reused for type inference (`z.infer<typeof schema>`).
- Validate at the boundary: parse API responses that come from outside the generated client with Zod.
- Use `@enterprise/ui` form fields wired via the `Form*` adapters; show field errors and a summary for a11y.

## API client
- Never edit `src/api/generated/**`; run `pnpm api:generate` after the backend OpenAPI spec changes.
- Base URL, auth headers, correlation IDs, and retries are configured once in app-shell — don't add interceptors in features.
- No PII in query keys, URLs, or telemetry attributes.
