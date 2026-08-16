---
alwaysApply: true
---

# Code Review — Review That Matters

## Order of attention

1. **Correctness** — logic errors, off-by-one, wrong conditions, null/undefined paths
2. **Security** — injection, exposed secrets, unsafe input handling
3. **Error handling** — swallowed errors, missing failure paths
4. **Edge cases** — boundaries, empty inputs, concurrency
5. **Maintainability** — naming, duplication, dead code, complexity
6. **Style** — conventions last; it's the least important if the code works

## How to give feedback

- Reference code precisely: `file:line`
- Prefer questions over commands for style/design ("Why is this needed?") — reserve commands for actual bugs
- Point at the behavior that's wrong, not the person who wrote it
- Separate blocking issues from nits; nits don't block
- Respect scope — note out-of-scope issues separately, don't block on them

## What to check

- No hardcoded secrets or credentials
- Proper error handling — nothing silently swallowed
- Input validation present at trust boundaries
- Types explicit where the codebase uses TypeScript
- No unused imports, variables, or dead code
- Tests exist for new behavior and regressions
