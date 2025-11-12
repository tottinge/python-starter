# Starter Kit

A Python 3.13+ project using `uv` for dependency management.

## Development Scripts

### `./clean_start`

Prepares your development environment for work:
- Pulls latest changes from remote (if configured)
- Syncs dependencies via `uv sync`
- Updates the pre-commit hook if needed
- Runs `./check` to verify everything works

Run this at the start of each coding session.

### `./check`

Validates code quality and correctness:
- Verifies code formatting with `black`
- Upgrades Python syntax to 3.13+ standards with `pyupgrade`
- Lints code with `ruff`
- Runs test suite with `pytest`
- Shows what would be cleaned by `git clean`

All checks must pass before committing.

### `./fixup`

Automatically fixes code issues:
- Upgrades Python syntax to 3.13+ with `pyupgrade`
- Auto-fixes linting issues with `ruff`
- Formats code with `black`

Run this when `./check` reports fixable issues.

### `scripts/pre-commit`

Git hook that runs `./check` before each commit. Automatically installed by `./clean_start`.

## Workflow

1. Start: `./clean_start`
2. Code and test
3. Fix issues: `./fixup`
4. Verify: `./check`
5. Commit (pre-commit hook runs automatically)
