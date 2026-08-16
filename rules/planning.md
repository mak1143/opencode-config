---
alwaysApply: true
---

# Planning — Think Before You Build

## Search first, build second

Before writing any code, understand what already exists.

1. Use Glob to find files matching the pattern you need
2. Use Grep to search for existing implementations of the same idea
3. Read surrounding files to understand the project structure
4. Only then begin implementation

Do not skip exploration. Most tasks have existing code that should be extended, not rewritten.

## Decompose complex tasks

When a task has 3+ distinct steps, use TodoWrite to track progress.

- Create todos before starting work
- Mark exactly one task `in_progress` at a time
- Mark a task `completed` only after verification (lint, test, or manual check)
- If blocked, keep the current task `in_progress` and add a follow-up describing the blocker

## Understand before editing

Before modifying a file:

- Read the file fully — do not assume its structure
- Identify the framework, library, and patterns in use
- Check imports to understand what dependencies are available

## Respect scope

- Do exactly what was asked — nothing more, nothing less
- If you discover a related issue, mention it but do not fix it unless asked
- If the user asks for X, do not also do Y and Z "while you're at it"
- When in doubt, ask before expanding scope

## Plan before complex changes

For tasks touching multiple files or systems:

- Outline the approach in plain text before making changes
- Identify the order of operations (what depends on what)
- Consider rollback — what needs to be undone if something fails
