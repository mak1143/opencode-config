---
alwaysApply: true
---

# Quality — Verify Before You Ship

## Always run verification

After making code changes, always run the project's verification commands.

- Run lint if available (eslint, ruff, clippy, etc.)
- Run typecheck if available (tsc, mypy, etc.)
- If both exist, run both
- If commands fail, fix the errors before reporting completion

If you don't know the correct command, ask the user. Suggest adding the command to AGENTS.md so you remember next time.

## Don't assume the test framework

- Check README, package.json scripts, or search for test files
- Look for patterns like `*.test.*`, `*_test.*`, `spec/`, `tests/`
- Use whatever framework the project already uses
- Never introduce a new testing framework without asking

## Verify your work

Before considering a task complete:

- Re-read the changed files to confirm correctness
- Check that imports resolve and types align
- If the change is behavioral, verify with a test or manual check
- If the change is visual, verify with a screenshot or description

## Run from the right place

- Use the `workdir` parameter instead of `cd` in bash commands
- Some commands only work from the project root
- Check where `package.json`, `Cargo.toml`, `pyproject.toml` live
- If unsure, run from the workspace root

## When verification is impossible

If you cannot run tests or lint:

- State this clearly: "Unable to verify — no test runner available"
- Explain what you checked manually
- Suggest how the user can verify

## Don't skip verification

- Running `git status` is not verification
- Reading a file is not verification
- Compilation/linting/testing is verification
- If you can't verify, say so — don't imply you did
