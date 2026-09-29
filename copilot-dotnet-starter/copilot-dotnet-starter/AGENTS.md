# AGENTS.md

The primary instructions for AI agents working in this repository live in
[`.github/copilot-instructions.md`](.github/copilot-instructions.md) and the scoped rules in
[`.github/instructions/`](.github/instructions/). Read those first — they are the source of truth.

## Agent quick reference
- Build: `dotnet build -warnaserror`
- Test: `dotnet test`
- Format: `dotnet format --verify-no-changes`
- All three must pass before you consider a task done.

## Guardrails for autonomous changes
- Keep PRs small and focused on one task; do not refactor unrelated code.
- Never modify: `src/<Service>.Api/Program.cs` composition order, `Directory.Packages.props`, CI workflows, or `/infra` — propose changes in the PR description instead.
- Add or update tests for every behavior change.
- Update the relevant ADR or README when you change an architectural decision.
