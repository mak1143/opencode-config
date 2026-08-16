---
alwaysApply: true
---

# Foundation — Entry Point

This is the entry point for the entire rule system. Every `.md` file in this directory is auto-loaded into every session via the `instructions` glob in `opencode.json`. Rules don't chain or import — they coexist, each owning one responsibility.

## How rules load

- Every file in `rules/*.md` is loaded into context automatically
- All rules here use `alwaysApply: true` — they're always active
- Rules supplement the agent's training — they don't replace it
- New rules can be added anytime — the glob picks them up

## The workflow lifecycle

All rules are always loaded into every session via `alwaysApply: true`. The lifecycle below shows when each rule matters most — not when it activates.

```
IDEA → PLAN → BUILD → VERIFY → DOCUMENT → COMMIT
 │       │       │        │          │          │
 ▼       ▼       ▼        ▼          ▼          ▼
ideas  plan-   coding   quality   documen-   git
.md    ning.md  .md      .md      tation.md  .md
```

| Phase | What happens | Rules that matter most |
|---|---|---|
| **Idea** | Explore, brainstorm, evaluate tradeoffs | `ideas.md` |
| **Plan** | Search existing code, decompose, scope the work | `planning.md` |
| **Build** | Write code matching project conventions | `coding.md` |
| **Verify** | Lint, typecheck, run tests | `quality.md` |
| **Document** | Update READMEs, changelogs, explain tools with history | `documentation.md` |
| **Commit** | Inspect, stage, message, push only when asked | `git.md` |

**Always relevant** (every phase):

- `output.md` — governs how responses are delivered: conciseness, formatting, no filler
- `context7.md` — use Context7 MCP for any library, framework, API, or CLI tool reference

**Domain-specific** (relevant when the task involves):

- `graphic-design.md` + `ui-ux.md` — pointers to `design-system` and `ui-ux-expert` skills
- `job-search.md` — generating professional content (resumes, cover letters, LinkedIn)

## Rule index

| Rule | One-line summary |
|---|---|
| `context7.md` | Use Context7 MCP for current library/framework docs |
| `planning.md` | Think before building, decompose, stay scoped |
| `coding.md` | Match conventions, preserve style, security basics |
| `quality.md` | Always verify with lint, typecheck, and tests |
| `output.md` | Be concise, no filler, precise code references |
| `git.md` | Only commit when asked, inspect status/diff/log first |
| `graphic-design.md` | Pointer to design-system and ui-ux-expert skills |
| `ui-ux.md` | Pointer to ui-ux-expert and design-system skills |
| `job-search.md` | Professional content: resume, LinkedIn, interviews, portfolio |
| `documentation.md` | Write docs like you maintain them, include tool history |
| `ideas.md` | Brainstorm, capture, decide with structured tradeoffs |

## Priority and conflicts

When two rules seem to conflict, apply this hierarchy:

1. **The more specific rule wins** — `documentation.md` overrides `coding.md`'s "no comments" when the task is documenting a public API
2. **`output.md` always applies** — it governs delivery format, not content decisions
3. **`quality.md` gates completion** — no task is done until verified
4. **When truly ambiguous** — ask the user rather than guessing

### Example conflict resolution

- `coding.md` says "never add comments" — but `documentation.md` says "document public APIs with docstrings"
- **Resolution:** The task determines which rule applies. If writing a library, document the API. If writing application code, skip comments.
- `git.md` says "only commit when asked" — but the user says "fix and commit"
- **Resolution:** "and commit" is explicit. Commit.

## When rules don't apply

- Rules are guidelines, not laws — common sense overrides
- If a rule prevents completing the user's request, note the exception and proceed
- Experimental or throwaway code may skip `quality.md` verification — state this explicitly
- One-off scripts may skip `documentation.md` — but a one-liner summary in the file is still good practice

## Adding new rules

To add a new rule:

1. Create a `.md` file in `rules/`
2. Add frontmatter: `alwaysApply: true` or a `condition`
3. Write imperative instructions: "Always X", "Never Y", "When Z, do W"
4. Keep under 150 lines — long rules dilute focus
5. Verify no overlap with existing rules — check the index above

The glob `rules/*.md` picks up new files automatically. No config changes needed.
