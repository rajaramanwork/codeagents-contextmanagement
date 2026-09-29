---
agent: "ask"
description: "Review the current UI changes against enterprise front-end standards"
---
Review the selected code or current changes against this repository's instructions.

Check, in priority order:
1. **Security** — XSS (`dangerouslySetInnerHTML`, unsanitized URLs), tokens/PII in storage, logs, URLs, or query keys.
2. **Accessibility** — semantics, labels, keyboard/focus, color contrast via tokens, missing axe tests.
3. **Architecture** — cross-feature imports, fetching outside Query hooks, server data in Zustand, edits to app-shell or generated code.
4. **Design system** — re-implemented primitives, hard-coded colors/spacing, non-approved UI libraries.
5. **Correctness & performance** — effect misuse, unstable keys, waterfalls, missing error/empty states, large bundle imports.
6. **i18n & tests** — hard-coded strings, missing behavior tests.

Output a table: `Severity (High/Med/Low) | File:Line | Issue | Suggested fix`.
Skip formatting issues handled by Prettier/ESLint. If nothing significant is found, say so.
