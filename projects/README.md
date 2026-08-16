# projects/

Per-project configuration overrides. Each subdirectory contains project-specific rules, skills, memory, and settings that activate only when working in that project's directory.

## How it works

- Each subdirectory = one project
- Name the directory to match the project's root folder or repo name
- Files here supplement (not replace) the global config
- Only the matching project's files are loaded when working in that project

## Directory structure

```
projects/
├── my-web-app/
│   ├── rules.md             # Project-specific rules
│   ├── memory.md            # Project context and decisions
│   └── skills/              # Project-specific skills
│       └── deploy/
│           └── SKILL.md
├── my-api/
│   ├── rules.md
│   └── memory.md
└── README.md
```

## File format

### rules.md

```markdown
---
project: my-web-app
---

# My Web App — Project Rules

## Stack
- Next.js 15 + App Router
- Prisma + PostgreSQL
- Tailwind CSS + shadcn/ui

## Conventions
- Use Server Components by default
- Client Components only when: interactivity, browser APIs, or hooks
- All pages must have metadata exported
- API routes must validate with Zod
```

### memory.md

```markdown
---
project: my-web-app
lastUpdated: 2025-07-11
---

# My Web App — Context

## Current Sprint
- [ ] Implement user authentication
- [ ] Add payment integration with Stripe
- [ ] Optimize Lighthouse score to 90+

## Architecture Decisions
- 2025-07-01: Chose Prisma over Drizzle for type safety
- 2025-06-28: Migrated from Pages Router to App Router
```

## Ideas for projects

| Project | Focus |
|---|---|
| `my-web-app/` | Frontend-specific rules, component conventions |
| `my-api/` | API design patterns, endpoint documentation |
| `my-cli/` | CLI tool conventions, argument parsing, output formatting |
| `my-lib/` | Library publishing, versioning, API surface rules |

## Rules

- One directory per project — keep them isolated
- `rules.md` and `memory.md` are the core files
- Use `project` in frontmatter to identify which project this config belongs to
- Project configs supplement global configs — they don't replace them
- Keep project configs lightweight — only override what differs from global
