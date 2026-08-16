---
name: refactorer
description: Identify and apply refactoring patterns to improve code structure without changing behavior. Use when the user asks to clean up code, reduce complexity, or improve maintainability.
---

# Refactorer

## Purpose

Improve code structure, readability, and maintainability through targeted refactoring. Every refactoring must preserve existing behavior — verified by tests before and after.

## When to use

- User says "refactor this" or "clean up this code"
- User identifies code smells: long functions, deep nesting, duplication
- User wants to extract a module, class, or function
- User asks to reduce complexity or improve readability
- User wants to apply a design pattern

## Workflow

### Step 1: Understand the code

- Read the full file and its callers
- Understand what the code does and why it's structured this way
- Check for existing tests that verify current behavior
- Identify the specific code smell or improvement target

### Step 2: Verify existing behavior

- Run existing tests to establish baseline
- If no tests exist, write characterization tests first
- Document the current behavior you need to preserve
- Identify all callers and dependents of the code

### Step 3: Apply refactoring

- Make one refactoring change at a time
- Use small, incremental steps — not big-bang rewrites
- Rename, extract, move, or restructure as needed
- Run tests after each change

### Step 4: Verify and clean up

- Run full test suite — all tests pass
- Check that no new warnings or type errors appeared
- Verify the code is actually simpler/better than before
- Remove dead code, unused imports, and stale comments

## Best practices

1. Refactor only when tests exist — or write characterization tests first
2. One refactoring at a time — don't rename and extract in the same step
3. Use your IDE's refactoring tools (rename, extract method) over manual edits
4. Preserve all behavior — refactoring changes structure, not behavior
5. If tests break, revert the last change — don't "fix" the tests
6. Keep commits atomic — one refactoring per commit
7. Don't refactor and add features in the same change

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Refactoring without tests | No safety net — behavior may change silently |
| Multiple refactorings in one step | Can't isolate which change broke something |
| "While I'm here" feature additions | Mixes refactoring with new behavior |
| Refactoring dead code | Waste of time — delete it instead |
| Over-engineering with patterns | Patterns are tools, not goals |
| Renaming without searching callers | Breaks downstream code |

## Expected output

1. **Refactored code** — simpler, more readable, same behavior
2. **Test results** — all existing tests still pass
3. **Change summary** — what was refactored and why
4. **Risk notes** — any callers or edge cases affected
5. **Before/after comparison** — complexity metrics, line count, nesting depth
