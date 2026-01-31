# Repository Guidelines

## Project Structure & Module Organization
The Python package lives in `src/runbook/`, with CLI/TUI code expected under
`src/runbook/cli/`. Documentation is in `docs/`, notably
`docs/concept.md` (product intent) and `docs/example_command_config.md` (YAML
configuration example). Tests should live in `tests/` (not yet present). The
`src/runbook.egg-info/` directory is generated packaging metadata; avoid manual
edits.

## Build, Test, and Development Commands
- `python -m venv .venv && source .venv/bin/activate` to create/activate a local
  virtual environment.
- `pip install -e ".[dev]"` to install runtime + dev dependencies.
- `pytest` to run tests using the project defaults (`-q`, `tests/`, `src` on
  `PYTHONPATH`).
- `ruff check .` to run linting with the configured rules (line length 80).
- `pyright` to run static type checks (Python 3.12, standard mode).
- Packaging uses setuptools; if you have `build` installed, `python -m build`
  produces distributions.

## Coding Style & Naming Conventions
Use Python 3.12 and PEP 8 conventions with 4-space indentation. Keep lines at
80 characters (Ruff config). Prefer `snake_case` for modules/functions and
`PascalCase` for classes. Imports should follow Ruff/Isort ordering with
`runbook` treated as first-party.

## Testing Guidelines
Use `pytest` and place tests under `tests/` with files named `test_*.py`. Add
tests for new behavior (CLI flows, config parsing) and keep them fast and
deterministic. If a change affects the YAML command format, update or add a
focused test and document the example in `docs/`.

## Commit & Pull Request Guidelines
Commit history uses short, typed messages like `chore: первоначальная настройка
проекта`; follow the same `type: summary` pattern when possible. Pull requests
should include: a concise description, linked issues (if any), the tests or
lint/typecheck commands run, and screenshots for UI/TUI changes.
