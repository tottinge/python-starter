# TDD Process Guide

## Core Principles

1. **Test-First Development**: Write tests before implementation
2. **Small Increments**: Make small changes between commits
3. **Continuous Verification**: Run tests after every change
4. **No Commits Without Passing Tests**: All tests must pass before committing

## Development Workflow

### Red-Green-Refactor Cycle

1. **Red**: Write a failing test
   ```bash
   uv run pytest
   ```
   - Verify the test fails for the right reason
   - Keep the test focused and small

2. **Green**: Make the test pass
   - Write minimal code to pass the test
   - Run tests immediately after the change
   ```bash
   uv run pytest
   ```

3. **Refactor**: Improve the code
   - Clean up implementation
   - Run tests after each refactoring step
   - Ensure all tests still pass

### Commit Guidelines

- **Tests must pass**: Cannot commit unless all tests are running and reporting success
- **Small batches**: Keep changes small between commits
- **Conventional commits**: Use conventional commit format
  - Examples: `feat: add user validation`, `test: add edge case for parser`
- **Concise messages**: Keep to one line when possible
- **LLM policy**: The LLM will never issue commit statements - commits are always made by the human developer

### When to Reset

If the scope of change becomes too large:
- Consider doing a hard reset (`git reset --hard`)
- Start over with smaller units of work
- Break the problem into smaller, testable increments

## Test Configuration

- Use TAP format for clear test result trees
- Run all tests before any commit
- All custom code must have unit tests
- Tests must be running (not skipped or disabled)

## Pre-Commit Checklist

- [ ] Tests passing
- [ ] Tests run after every change
- [ ] No skipped or disabled tests
- [ ] Changes are small and focused
- [ ] Commit message follows conventional format

## Commands

### Project Scripts

```bash
# Start a work session (pulls latest, syncs dependencies, runs checks)
./clean_start

# Run all checks (formatting, linting, tests)
./check

# Auto-fix code issues (pyupgrade, ruff, black)
./fixup
```

### Direct Commands

```bash
# Run all tests
uv run pytest

# Run tests with TAP output
uv run pytest --tap-stream

# Run specific test file
uv run pytest tests/test_module.py

# Run with coverage
uv run pytest --cov

# Format code
black .

# Lint code
ruff check .
```

### Typical Workflow

1. Start your session: `./clean_start`
2. Write a failing test
3. Run tests: `uv run pytest`
4. Implement code to pass the test
5. Run tests again: `uv run pytest`
6. Auto-fix formatting: `./fixup` (if needed)
7. Verify everything: `./check`
8. Commit with conventional commit message

## Anti-Patterns to Avoid

- ❌ Writing multiple features before running tests
- ❌ Committing with failing tests
- ❌ Making large, sweeping changes
- ❌ Skipping the refactor step
- ❌ Writing tests after implementation
- ❌ Committing without running the full test suite
