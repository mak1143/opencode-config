---
name: doc-writer
description: Generate project documentation — READMEs, API docs, docstrings, and changelogs. Use when the user asks to write docs, document code, or create a README.
---

# Doc Writer

## Purpose

Produce accurate, audience-appropriate documentation as a deliverable. This skill handles the workflow of generating docs. For documentation standards and conventions, see the `documentation.md` rule.

## When to use

- User says "write a README" or "document this project"
- User needs API documentation or endpoint descriptions
- User wants docstrings added to functions or classes
- User asks to document a CLI tool or library
- User needs a changelog entry

## Workflow

### Step 1: Understand the project

- Read the codebase structure and entry points
- Identify the target audience (developers, end users, ops)
- Check for existing documentation — what's missing or outdated?
- Understand what the project does from the code, not assumptions

### Step 2: Choose the documentation type

- **README** — project overview, quick start, usage
- **API docs** — endpoint descriptions, parameters, examples
- **Docstrings** — function/method documentation for developers
- **Architecture** — system design, component relationships
- **Changelog** — version history with meaningful descriptions

### Step 3: Write

- Start with the one-liner: what does this project do?
- Include runnable examples — not just descriptions
- Write for the reader's context — don't assume knowledge
- Use concrete examples over abstract descriptions

### Step 4: Verify

- Test all code examples — they must run
- Check that commands work from a clean environment
- Verify links point to the correct resources

## Best practices

1. Use imperative mood: "Run `pip install`", not "You should run"
2. For documentation standards and conventions, follow the `documentation.md` rule

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Documenting what the code does | The code shows what — docs should explain why |
| Untested code examples | Broken examples erode trust |
| Assuming reader knows the project | First-time users need orientation |
| Walls of text without structure | Headers, lists, and code blocks aid scanning |
| Stale documentation | Worse than no documentation — leads users astray |

## Expected output

1. **README.md** — project overview with runnable quick start
2. **Docstrings** — public API documentation with examples
3. **API reference** — endpoint descriptions with parameters and responses
4. **Architecture notes** — if complex, component relationships documented
5. **Changelog** — version history in Keep a Changelog format
