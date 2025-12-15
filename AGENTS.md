# Repository Guidelines

## Project Structure & Module Organization

- `.agent/rules/`: Antigravity Workspace Rules (Markdown).
- `.agent/workflows/`: Antigravity Workflows (Markdown), invoked via `/workflow-name`.
- `README.md`: User-facing instructions for using these Rules/Workflows in Antigravity.
- Legacy Gemini CLI extension (optional): `gemini-extension.json`, `blueprint.md`, `commands/blueprint/*.toml`.

## Build, Test, and Development Commands

This repository is prompt/config driven—there is no build step.

- Antigravity smoke test (manual):
  - Enable the Workspace rule in `.agent/rules/blueprint.md`.
  - Run `/blueprint-plan <goal>` and confirm `PLAN.md` is created and approval is requested.
  - Run `/blueprint-define` → `TODO.md`, then `/blueprint-implement` → `ACT.md`, and `/blueprint-test` → `TEST.md`.

Legacy Gemini CLI (only if you still use it):
- Install: `gemini extensions install .`
- Update: `gemini extensions update blueprint`
- Uninstall: `gemini extensions uninstall blueprint`

## Coding Style & Naming Conventions

- In `.agent/rules/*.md` and `.agent/workflows/*.md`, keep text short, imperative, and unambiguous.
- Workflow filenames should match the invoked command (e.g., `.agent/workflows/blueprint-plan.md` → `/blueprint-plan`).
- Treat workflow state filenames as part of the “API”; keep them consistent (`RESEARCH.md`, `PLAN.md`, `TODO.md`, `ACT.md`, `TEST.md`).
- Keep Rules/Workflows under Antigravity’s 12,000-character limit per file.

## Testing Guidelines

There are no automated tests in this repo. Prefer a quick manual smoke test in a scratch workspace using the commands listed above. If you add tooling/tests in the future, document them in `README.md`.

## Commit & Pull Request Guidelines

- Follow the existing Git history’s conventions: Conventional Commits where practical (`feat: ...`, `fix: ...`, `docs: ...`).
- PRs should explain user-visible workflow changes, link relevant issues, and update `README.md` when commands or file conventions change.
- Bump `gemini-extension.json` `version` when making a release-worthy change.

## Security & Safety Notes

Rules and workflows should preserve a safety posture: require explicit confirmation before destructive actions and maintain “plan before acting”.
