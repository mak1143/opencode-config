---
alwaysApply: true
---

# Testing — Write and Maintain Tests

## Match the existing setup

- Never introduce a new testing framework without asking
- Check README, package.json scripts, or existing `*.test.*` / `*_test.*` / `spec/` files
- Run tests the way the project already runs them

## Naming and structure

- Name tests to describe the behavior: `test("rejects invalid email")` not `test("works")`
- Put tests next to source (`foo.test.ts`) or in `tests/` — follow the existing layout
- One behavior per test — don't bundle unrelated assertions

## What to test

- Happy path, error paths, and edge cases (boundaries, empty, null, duplicates)
- Assert outcomes and results, not implementation details
- If a bug was fixed, add a regression test for it

## Mocking

- Mock at boundaries only: HTTP, database, filesystem, time
- Don't mock what you don't own (third-party API contracts stay real or stubbed thin)
- Keep mocks small — over-mocking hides real bugs

## Failing tests

- Fix the code, not the test — never delete or weaken a test to make it pass
- If the test itself is wrong, say so explicitly and fix the test
- Run the full suite after changes to catch regressions

## When tests aren't possible

- State it clearly: "No test runner available — verified manually"
- Describe what you checked by hand and how the user can verify
