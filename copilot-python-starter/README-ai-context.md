# AI Context Starter Kit: GitHub Copilot (Python)

| Priority | File | Loaded | Purpose |
|---|---|---|---|
| 1: Must | `.github/copilot-instructions.md` | Always | Stack, layout, uv commands, non-negotiables |
| 2: Must | `.github/instructions/python.instructions.md` | `src/**/*.py` | Typing, errors, async, logging, DI |
| 3: Must | `.github/instructions/api.instructions.md` | `api/**`, `main.py` | FastAPI routers, schemas, auth, errors |
| 4: Must | `.github/instructions/data-access.instructions.md` | repositories, migrations, jobs | SQLAlchemy 2.0, Alembic, Snowflake, batch jobs |
| 5: Must | `.github/instructions/tests.instructions.md` | `tests/**` | pytest, fakes, respx, Testcontainers |
| 6: If AI | `.github/instructions/genai.instructions.md` | `llm/**`, `prompts/**` | enterprise-genai, structured output, guardrails, evals |
| 7: Should | `AGENTS.md` | Coding agent / CLI | Pointer + agent guardrails |
| 8: Should | `.github/prompts/new-endpoint.prompt.md` | `/new-endpoint` | Scaffold a feature end-to-end |
| 9: Nice | `.github/prompts/code-review.prompt.md` | `/code-review` | Standards-based review |
| 10: Nice | `.github/agents/arb-reviewer.agent.md` | Select agent | Read-only ARB compliance review |

## Adopting
1. Copy into the repo root; replace `<placeholders>`, package names (`enterprise-defaults`, `enterprise-genai`), and ADR IDs.
2. Pure data/ETL repos: drop `api.instructions.md` and `new-endpoint.prompt.md`; keep data-access and genai.
3. Swap stack choices you don't use (e.g. mypy instead of Pyright, Poetry instead of uv); stale rules are worse than none.
4. Verify frontmatter keys against your Copilot/VS Code version (prompt-file `agent:` was formerly `mode:`).
5. Own these files via CODEOWNERS and review changes like code.
