---
name: debug
description: Helps investigate software bugs systematically using a structured workflow — reproduce, isolate, diagnose, fix, verify. Use when the user reports a bug, error, or unexpected behavior.
---

# Debug — Systematic Bug Investigation

## Purpose

Find the root cause of a bug through structured investigation, not guessing. Every fix must be backed by understanding. If you can't reproduce it, you can't fix it.

## When to use

- User reports an error, exception, or stack trace
- User says "this isn't working" or "something is wrong"
- User mentions a regression or behavior change
- User asks to debug or investigate a specific issue

## Workflow

### Step 1: Reproduce

Before touching any code, reproduce the bug.

- Ask the user for exact steps to reproduce
- Ask for the error message or unexpected output
- Ask about environment: OS, language version, framework version
- Check if the bug is intermittent or consistent
- If you can't reproduce, say so — don't guess

### Step 2: Isolate

Narrow down where the bug lives.

- Read the stack trace — identify the exact file and line
- Trace the call path from the error point backward
- Check if the bug is in your code, a dependency, or configuration
- Use `grep` to find related code paths
- Check recent changes: `git log --oneline -10`, `git diff`

### Step 3: Diagnose

Understand why the bug exists.

- Read the code at the error point and its callers
- Check assumptions: what does the code expect vs. what actually happens?
- Look for type mismatches, null/undefined, race conditions, off-by-one errors
- Check if the bug is a symptom of a deeper issue
- Verify with the user: "The bug happens because X — does that match what you see?"

### Step 4: Fix

Apply the minimal fix that addresses the root cause.

- Fix the cause, not the symptom
- Make the smallest change that resolves the issue
- Don't refactor unrelated code "while you're at it"
- If the fix is in a dependency, report it — don't patch vendor code
- If multiple fixes are possible, present options with tradeoffs

### Step 5: Verify

Confirm the fix works and doesn't break anything.

- Run the original reproduction steps — bug should be gone
- Run existing tests — nothing should break
- If no tests exist, write one that catches this bug
- Check edge cases related to the fix
- Verify no regressions in adjacent functionality

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Guessing without reproducing | You might fix the wrong thing |
| Changing multiple things at once | You won't know which change fixed it |
| Reading code without running it | Assumptions compound — verify with execution |
| Ignoring the stack trace | It tells you exactly where the error happens |
| Fixing the symptom | The bug will resurface in a different form |
| Skipping verification | The fix might work for this case but break others |
| Not checking recent changes | Most bugs are introduced recently |

## Expected output

When completing a debug session, deliver:

1. **Root cause** — one sentence explaining why the bug happens
2. **Evidence** — the file, line, and code that causes it
3. **Fix** — the specific change made (or recommended)
4. **Verification** — how you confirmed the fix works
5. **Prevention** — what could prevent this class of bug (test, lint rule, type guard)
