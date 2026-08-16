---
name: test-writer
description: Generate comprehensive tests for existing Python code using pytest, unittest, or other frameworks. Use when the user asks to write tests, improve coverage, or create test suites.
---

# Test Writer

## Purpose

Generate meaningful tests that catch real bugs, not just happy-path coverage. Tests should be readable, maintainable, and serve as documentation for expected behavior.

## When to use

- User says "write tests for this" or "add test coverage"
- User has code with no tests or low coverage
- User wants to test a specific function, class, or module
- User needs integration tests for API endpoints
- User asks to test edge cases or error conditions

## Workflow

### Step 1: Understand the code

- Read the target code fully — understand inputs, outputs, side effects
- Identify public API surface vs internal helpers
- Check for existing tests — what's already covered?
- Identify the test framework in use (pytest, unittest, etc.)
- Check for existing fixtures, conftest.py, test utilities

### Step 2: Design the test suite

- Map each public function/method to test cases
- Identify happy path, edge cases, and error conditions
- Plan fixtures for shared setup (database, API clients, mock data)
- Decide: unit tests (isolated) vs integration tests (real dependencies)

### Step 3: Write the tests

- Use descriptive test names: `test_login_with_invalid_password_returns_401`
- One assertion per test when possible (or one logical concept)
- Use fixtures and factories for test data — never hardcode in tests
- Mock external services (APIs, databases) at the boundary
- Test both success and failure paths

### Step 4: Verify

- Run the test suite — all tests pass
- Check coverage on the target code (`pytest --cov`)
- Verify tests are actually testing something (not just passing trivially)
- Ensure tests are independent — no order dependency

## Best practices

1. Test behavior, not implementation — what it does, not how it does it
2. Use `Arrange → Act → Assert` pattern for test structure
3. Use `parametrize` for multiple inputs with the same logic
4. Mock at the edges, not in the middle — mock external services, not internal functions
5. Use factories (`factory_boy`, `pytest.fixture`) for test data
6. Test edge cases: empty inputs, None values, boundary conditions
7. Keep tests fast — slow tests get skipped
8. Name test files `test_<module>.py` or `<module>_test.py`

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Testing implementation details | Tests break when code is refactored correctly |
| One giant test function | Can't isolate which part failed |
| Hardcoded test data | Tests become brittle and hard to maintain |
| Mocking too much | Tests pass but don't verify real behavior |
| No edge case testing | Bugs hide in boundary conditions |
| Tests depend on execution order | Random failures in different test runners |
| Ignoring error paths | Only happy path is tested, errors slip through |

## Expected output

1. **Test file** — follows project naming convention, imports correctly
2. **Test cases** — covering happy path, edge cases, and error conditions
3. **Fixtures** — reusable test data setup in conftest.py
4. **Coverage report** — which lines/branches are covered
5. **Documentation** — test names serve as executable specifications
