---
applyTo: "src/**/*.tsx"
description: "React component standards — structure, hooks, accessibility, i18n"
---
# React component standards

## Structure
- Function components only; named exports (no default exports except route files that require them).
- One component per file; file name = component name in PascalCase (`OrderSummary.tsx`).
- Props typed with a `type XxxProps = {...}`; no `React.FC`. Destructure props in the signature.
- Keep components presentational; move data fetching and logic into `useXxx` hooks in `hooks/` or `api/`.
- Components > ~150 lines or with > 3 responsibilities → split.
- Route components are thin: read params/loader data → render feature components.

## Hooks & rendering
- Follow the Rules of Hooks; `eslint-plugin-react-hooks` must pass without disabling.
- Don't sync props to state; derive values during render.
- Avoid `useEffect` for data fetching or derived state. Effects only for true external sync (subscriptions, DOM APIs).
- Don't add `useMemo`/`useCallback` by default — the React Compiler handles memoization; add only with a measured reason.
- Stable, meaningful `key`s — never array index for dynamic lists.
- Wrap feature roots in the app-shell `<FeatureErrorBoundary>` and use `<Suspense>` with `@enterprise/ui` skeletons.

## Accessibility (WCAG 2.2 AA)
- Semantic elements first (`button`, `nav`, `main`, `label`); no clickable `div`s.
- Every input has a visible `<label>` or `aria-label`; errors linked via `aria-describedby`.
- Full keyboard support; visible focus; return focus after closing dialogs (use `@enterprise/ui` `Dialog`).
- Images need `alt` (empty `alt=""` if decorative). Don't convey meaning by color alone.

## i18n
- All user-visible strings via `const { t } = useTranslation('<feature>')`; keys `feature.section.item`.
- Format dates/numbers/currency with `@enterprise/i18n` formatters, not manual string building.

## Example
```tsx
type OrderSummaryProps = { orderId: string };

export function OrderSummary({ orderId }: OrderSummaryProps) {
  const { t } = useTranslation('orders');
  const { data: order } = useOrderQuery(orderId); // suspense-enabled

  return (
    <Card aria-labelledby="order-summary-title">
      <Heading id="order-summary-title" level={2}>{t('orders.summary.title')}</Heading>
      <Text>{t('orders.summary.status', { status: order.status })}</Text>
      <Money value={order.total} currency={order.currency} />
    </Card>
  );
}
```
