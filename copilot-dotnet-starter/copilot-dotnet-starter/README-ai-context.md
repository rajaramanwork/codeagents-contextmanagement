# AI Context Starter Kit — GitHub Copilot (.NET)

| Priority | File | Loaded | Purpose |
|---|---|---|---|
| 1 — Must | `.github/copilot-instructions.md` | Always | Stack, layout, build/test, non-negotiables |
| 2 — Must | `.github/instructions/csharp.instructions.md` | `src/**/*.cs` | C# + Minimal API standards |
| 3 — Must | `.github/instructions/data-access.instructions.md` | Infrastructure/repos | DAL, EF Core/PostgreSQL, Dapper/Snowflake |
| 4 — Must | `.github/instructions/tests.instructions.md` | `tests/**` | Test conventions |
| 5 — Should | `AGENTS.md` | Coding agent / CLI | Pointer + agent guardrails (cross-tool) |
| 6 — Should | `.github/prompts/new-endpoint.prompt.md` | `/new-endpoint` | Scaffold a feature end-to-end |
| 7 — Nice | `.github/prompts/code-review.prompt.md` | `/code-review` | Standards-based review |
| 8 — Nice | `.github/agents/arb-reviewer.agent.md` | Select agent | Read-only ARB compliance review |

## Adopting
1. Copy into the repo root; replace every `<placeholder>`.
2. Delete rules that don't apply — every line in the always-on file costs tokens on every request.
3. Verify frontmatter keys against your Copilot/VS Code version (prompt-file `agent:` was formerly `mode:`).
4. Treat changes to these files like code: CODEOWNERS + PR review.
