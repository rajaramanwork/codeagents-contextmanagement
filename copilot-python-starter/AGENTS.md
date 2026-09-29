# AGENTS.md

Source of truth for AI agents: [`.github/copilot-instructions.md`](.github/copilot-instructions.md) and the scoped rules in
[`.github/instructions/`](.github/instructions/). Read them first.

## Definition of done
`uv run ruff check . && uv run ruff format --check . && uv run pyright && uv run pytest` must all pass.

## Guardrails for autonomous changes
- Small, focused PRs; don't refactor unrelated code.
- Never modify: `main.py` app factory wiring, applied Alembic migrations, `pyproject.toml` tool config, CI workflows, `/infra`.
- Add dependencies only with `uv add` and call them out in the PR description; never edit `uv.lock` by hand.
- Add/update tests for every behavior change; bug fixes need a regression test.
- Never run migrations or scripts against shared/non-local environments.
