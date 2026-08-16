---
alwaysApply: true
---

# Debugging — Find the Root Cause

## Work in order

1. **Reproduce** — you can't fix what you can't trigger. Get a reliable, minimal reproduction first.
2. **Read the full error** — message, file, line, stack trace, first failure point.
3. **Isolate** — bisect recent changes; binary-search the input until the failing case is minimal.
4. **Diagnose** — identify the root cause before editing. Patching symptoms creates new bugs.
5. **Fix** — one change at a time, then re-run the reproduction.
6. **Verify** — confirm the fix resolves the original issue and check for regressions.

## Habits

- Change one thing at a time — parallel fixes are untestable
- Use the debugger, logs, or a focused test to inspect state at the failure point
- Suspect your own code before blaming libraries, tools, or the environment
- Check recent changes first: `git diff`, `git log` — most bugs are introduced, not historical
- When stuck, explain the problem out loud (or to a colleague) — it reorders the brain

## Report

- Include the exact error message and `file:line` where it occurred
- State the likely cause in one sentence
- Suggest the fix — don't just describe the problem
