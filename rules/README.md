# rules/

Global rules and instructions that apply to every session. The `instructions` glob in `opencode.json` points to `rules/*.md` — all files here are loaded automatically.

## How it works

- Every `.md` file in this directory is loaded into context
- All rules use `alwaysApply: true` — they're always active
- Rules supplement the agent's training — they don't replace it

## File format

```markdown
---
alwaysApply: true
---

Your rule content here. Be specific and actionable.
```

## Existing rules

| File | Purpose |
|---|---|
| `foundation.md` | Entry point — explains the rule system, lifecycle, and conflict resolution |
| `planning.md` | Think before building, decompose, stay scoped |
| `coding.md` | Match conventions, preserve style, security basics |
| `quality.md` | Always verify with lint, typecheck, and tests |
| `output.md` | Be concise, no filler, precise code references |
| `git.md` | Only commit when asked, inspect status/diff/log first |
| `graphic-design.md` | Pointer to `design-system` and `ui-ux-expert` skills |
| `ui-ux.md` | Pointer to `ui-ux-expert` and `design-system` skills |
| `job-search.md` | Professional content: resume, LinkedIn, interviews, portfolio |
| `documentation.md` | Write docs like you maintain them, include tool history |
| `ideas.md` | Brainstorm, capture, decide with structured tradeoffs |
| `full-stack.md` | Load the frontend/backend learning references on demand |
| `context7.md` | Use Context7 MCP for current library/framework docs |

## Rules

- One rule per file — keep them focused and composable
- Write rules as imperative instructions: "Always X", "Never Y", "When Z, do W"
- Reference specific tools/libraries by name — avoid vague guidance
- Keep under 150 lines — long rules dilute focus
- Verify no overlap with existing rules — check the index above
