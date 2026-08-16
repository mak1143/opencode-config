---
description: Git workflow assistant — status, diff, branch, log, stash, rebase, merge
---
Assist the user with git operations. Run `git status` and `git branch` first to understand the current state. Then help with whatever the user needs:

- **Status/diff** — show working tree and staged changes
- **Branch management** — create, switch, merge, rebase, delete branches
- **Stashing** — save/apply/pop/drop working changes
- **Log/history** — view recent commits, search by author/message/file
- **Undo** — unstage, restore, reset (safe operations only — never force-push or rewrite public history)
- **Cherry-pick** — apply specific commits to current branch
- **Rebase** — interactive rebase, onto, conflict resolution help
- **PR workflow** — open, review, merge via `gh` CLI
- **Commit** — prepare a commit message from the current diff/status, matching the repo's existing style

Follow safety rules from `rules/git.md`: never commit/push/amend unless asked, never rewrite public history, always inspect before acting.
