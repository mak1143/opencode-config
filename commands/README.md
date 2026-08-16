# commands/

Custom slash-commands. Each `.md` file defines a reusable prompt template that can be invoked as `/command-name` during a session.

## How it works

- Each file = one slash-command
- The filename becomes the command name (e.g., `review.md` → `/review`)
- The file content is the prompt template sent to the agent
- Commands can accept arguments (passed as `$ARGUMENTS`)

## File format

```markdown
---
description: Review the specified code for bugs and improvements
arguments:
  - name: target
    description: File or directory to review
    required: true
---

Review the following code for bugs, security issues, and improvements:

Target: $ARGUMENTS

## Checklist
- [ ] No hardcoded secrets or credentials
- [ ] Proper error handling
- [ ] Input validation present
- [ ] Types are explicit
- [ ] No unused imports or variables
```

## Frontmatter options

| Field | Type | Required | Description |
|---|---|---|---|
| `description` | string | yes | What the command does (shown in help) |
| `arguments` | array | no | List of arguments the command accepts |
| `agent` | string | no | Override the agent type to use for this command |
| `model` | string | no | Override the model to use for this command |

## Ideas for commands

| Command | Purpose |
|---|---|
| `/review` | Code review with structured checklist |
| `/fix` | Diagnose and fix bugs |
| `/explain` | Explain the selected code in plain English |
| `/test` | Run tests with coverage |
| `/refactor` | Suggest and apply refactoring improvements |
| `/deploy` | Run deployment pipeline with safety checks |
| `/snapshot` | Create a commit with a descriptive message |
| `/deps` | Analyze dependencies for updates and vulnerabilities |
| `/optimize` | Profile and optimize the specified code |

## Rules

- One command per file
- Use `$ARGUMENTS` to reference user-provided input
- Keep prompt templates concise — under 30 lines
- Use `description` in frontmatter so users know what the command does
- Commands should produce a specific, actionable output
