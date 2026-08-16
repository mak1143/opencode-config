---
alwaysApply: true
---

# Git — Version Control Conventions

## Only commit when asked

Never commit, push, amend, or create PRs unless the user explicitly asks. If the user says "fix the bug", they did not say "fix the bug and commit".

## Pre-commit inspection

Before any commit, always run:

1. `git status` — see what changed
2. `git diff` — verify the actual changes
3. `git log --oneline -5` — understand recent history

Stage only the files that are part of the intended change. Never stage everything blindly.

## Commit messages

- Format commit messages as `/*|| <message> || */` (user preference)
- Keep the message concise — one line when possible
- Match the existing repo style (conventional commits, imperative mood, etc.)
- If the repo has no convention, use imperative mood: "Add feature" not "Added feature"
- Reference issue numbers when relevant: "Fix #123"

## Never commit secrets

See `coding.md` for security basics (no exposed secrets, validate input, parameterized queries).

Before staging any file, verify it does not contain API keys, tokens, passwords, or private config. If you find a secret, stop and tell the user immediately.

## Don't force history

- Never force-push unless explicitly asked
- Never amend previous commits unless explicitly asked
- Never rebase shared branches without asking
- Never skip git hooks

## Pull requests

Before creating a PR:

1. Check `git status` — no uncommitted changes
2. Check `git log` — review all commits included
3. Check the diff from the base branch
4. Review each commit for correctness

Use `gh` CLI for GitHub operations. Return the PR URL when done.

## Branch awareness

- Check which branch you're on before committing
- Don't commit directly to `main` or `master` unless the user asks
- If the task is a new feature, suggest creating a feature branch
