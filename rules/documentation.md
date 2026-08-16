---
alwaysApply: true
---

# Documentation — Write It Like You'll Maintain It

## Software history — explain why, not just what

When explaining or using a tool, library, or protocol, briefly cover its origin:

- **Why it was created** — what problem existed before it
- **What it replaced** — what people used before (and why that wasn't enough)
- **Why it matters today** — how it fits into modern workflows

### Format for tool explanations

```
[Tool] was created in [year] by [who] to solve [problem].
Before [tool], people used [alternative], which had [limitation].
Today it matters because [relevance to current task].
```

### Examples

**curl**
`curl` was created in 1998 by Daniel Stenberg to transfer data using URL syntax.
Before curl, users relied on `wget` (limited protocol support) or raw socket programming.
Today it matters because it's the universal Swiss Army knife for HTTP, FTP, and API testing.

**SSH**
SSH was created in 1995 by Tatu Ylönen to replace insecure remote login protocols (telnet, rlogin) that sent passwords in plaintext.
Before SSH, anyone on the network could intercept credentials.
Today it matters because it underpins secure remote server access, Git over HTTPS, and tunneling.

**REST APIs**
REST was defined in 2000 by Roy Fielding as part of his doctoral dissertation on web architecture.
Before REST, SOAP/XML-RPC dominated web services — heavyweight, tight coupling, verb-heavy.
Today it matters because REST's statelessness and resource-based design power most web APIs.

### When to include history

- User asks "what is X?" or "how does X work?"
- Introducing a tool that may be unfamiliar
- Comparing two approaches where history explains the tradeoff
- **Skip** if the user clearly knows the tool and just wants usage help

## READMEs — the front door

Every project should have a README.md. Structure:

1. **One-liner** — what this project does
2. **Quick start** — copy-paste commands to get running
3. **Usage** — how to use it (API, CLI, examples)
4. **Configuration** — env vars, config files, options
5. **Contributing** — how to contribute (if applicable)

### README rules

- Write for someone who has never seen this project
- Include runnable examples — not just descriptions
- Keep under 200 lines — link out for deep docs
- Update README when behavior changes — stale READMEs are worse than none
- No walls of text — use headers, lists, code blocks

## Inline documentation

- Document **why**, never **what** — the code shows what
- Use docstrings/JSDoc for public APIs, not internal helpers
- If a function name doesn't explain itself, rename it — don't comment it
- Document side effects, non-obvious parameters, and edge cases
- Skip comments that restate the code: `// increment counter` above `counter++`

### When inline docs are justified

- Complex algorithms (explain the approach, not each line)
- Business logic with non-obvious rules
- Public API surfaces consumed by others
- Workarounds or hacks with a known TODO to fix later

## Changelogs — what changed and why

Keep a `CHANGELOG.md` using [Keep a Changelog](https://keepachangelog.com) format:

```markdown
# Changelog

## [1.2.0] - 2025-07-11
### Added
- User authentication with JWT
- Stripe payment integration

### Fixed
- Race condition in concurrent form submissions

### Removed
- Deprecated `/legacy` endpoint

## [1.1.0] - 2025-06-15
### Added
- Dark mode toggle
```

### Changelog rules

- Group by version, sorted newest first
- Three categories: Added, Fixed, Changed, Deprecated, Removed, Security
- Write for humans — "Fixed login timeout" not "Updated auth.js"
- Reference issue/PR numbers where relevant
- Don't log every commit — log meaningful user-facing changes

## Architecture decisions

When making significant design choices, record the decision:

```markdown
# Decision: Use PostgreSQL over MongoDB

## Date: 2025-07-01

## Context
We need a database for user data with complex relationships.

## Decision
PostgreSQL with Prisma ORM.

## Consequences
+ ACID compliance for financial data
+ Prisma gives type-safe queries
- Migration overhead on schema changes
```

Store these in `memory/` or `projects/<name>/memory.md` — not in code comments.

## Documentation as deliverable

- If the task is "document X", treat it like code: research, draft, review, iterate
- Include examples that work — copy-paste and run, not hypothetical
- Link to official docs for accuracy
- Update docs when code changes — docs and code drift is a bug
