# skills/

Modular skill definitions. Each subdirectory contains a `SKILL.md` file that defines a reusable capability — a set of instructions activated conditionally based on the user's task.

## How it works

- Each subdirectory = one skill
- The directory must contain a `SKILL.md` file
- OpenCode discovers skills automatically from this directory
- Skills are activated when the user's task matches the skill's description

## Directory structure

```
skills/
├── my-skill/
│   ├── SKILL.md              # Required: skill definition
│   └── .agents/              # Optional: sub-agents for delegation
│       └── skills/
│           └── my-skill/
│               └── agent.md
├── another-skill/
│   └── SKILL.md
└── README.md
```

## SKILL.md format

```markdown
---
name: [kebab-case]
description: One-line purpose + when to activate
---

# [Title]

## Purpose
## When to use
## Workflow
## Best practices
## Common mistakes
## Expected output
```

## Naming conventions

- Use lowercase with hyphens: `api-client/`, not `ApiClient/`
- Keep names descriptive: `cache-strategy/` over `cache/`
- Match the directory name to the `name` field in frontmatter

## Skill index

### Backend

| Skill | Purpose |
|---|---|
| `api-designer/` | Design REST/GraphQL APIs with OpenAPI specs |
| `api-client/` | Consume APIs — auth, retries, pagination, error handling |
| `db-migrator/` | Schema migrations with rollback support |
| `debug/` | Systematic bug investigation and diagnosis |

### DevOps

| Skill | Purpose |
|---|---|
| `docker-optimizer/` | Dockerfile best practices, multi-stage builds, security |
| `ci-pipeline/` | GitHub Actions / GitLab CI configuration |

### Code Quality

| Skill | Purpose |
|---|---|
| `test-writer/` | Generate pytest/unittest tests from existing code |
| `refactorer/` | Identify and apply refactoring patterns safely |
| `security-auditor/` | OWASP checks, secret scanning, dependency CVEs, license audit |
| `perf-profiler/` | Performance profiling, bottleneck analysis, optimization |
| `cache-strategy/` | Caching patterns — invalidation, TTL, Redis, CDN |

### Documentation

| Skill | Purpose |
|---|---|
| `doc-writer/` | Generate READMEs, API docs, docstrings, changelogs |

### Design

| Skill | Purpose |
|---|---|
| `design-system/` | Build design systems with tokens, components, patterns |
| `icon-set/` | Create consistent SVG icon sets with naming conventions |

### Existing

| Skill | Purpose |
|---|---|
| `find-skills/` | Discover and install skills from the ecosystem |
| `frontend-design/` | Production-grade frontend interfaces |
| `grill-me/` | Stress-test plans and designs through questioning |
| `ui-ux-expert/` | UI/UX design intelligence across 10 stacks |
| `web-design-guidelines/` | Review UI code for web interface guidelines |

## Rules

- One skill per directory
- `SKILL.md` is required — OpenCode ignores directories without it
- Keep skills modular — each skill should be self-contained
- Use `description` field in frontmatter to help OpenCode match tasks to skills
- All skills follow the same format: Purpose → When to use → Workflow → Best practices → Common mistakes → Expected output
