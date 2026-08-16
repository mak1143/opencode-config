---
name: ci-pipeline
description: Design and configure CI/CD pipelines for GitHub Actions, GitLab CI, or similar platforms. Use when the user asks to set up continuous integration, deployment workflows, or automation gates.
---

# CI Pipeline

## Purpose

Create reliable CI/CD pipelines that catch issues early, deploy safely, and run fast. Every pipeline should have clear stages: lint, test, build, deploy. Speed matters — slow pipelines get skipped.

## When to use

- User says "set up CI" or "create a GitHub Actions workflow"
- User needs to automate testing, linting, or deployment
- User wants to add build gates or quality checks
- User asks to optimize a slow pipeline
- User needs multi-environment deployment (dev → staging → prod)

## Workflow

### Step 1: Understand the project

- Identify the language, framework, and build system
- Check for existing CI configuration (`.github/workflows/`, `.gitlab-ci.yml`)
- Understand the deployment target (Vercel, AWS, Docker, bare metal)
- Identify required checks: lint, typecheck, test, security scan

### Step 2: Design the pipeline

- Define stages: lint → test → build → deploy
- Decide triggers: push, PR, schedule, manual
- Plan caching: dependencies, build artifacts
- Set up matrix builds for multiple versions/platforms if needed

### Step 3: Implement

- Write the workflow configuration file
- Add dependency caching to speed up builds
- Configure secrets for deployment credentials
- Add status badges and notifications

### Step 4: Optimize

- Cache dependencies aggressively (pip, npm, cargo)
- Run independent jobs in parallel
- Skip unnecessary jobs based on changed files (`paths` filter)
- Set appropriate timeouts to prevent hung jobs

## Best practices

1. Run lint before test — catch style issues fast before expensive tests
2. Cache dependencies — don't reinstall on every run
3. Use matrix builds for multi-version testing
4. Pin action versions (`actions/checkout@v4`) — not `@main`
5. Store secrets in the platform's secret store — never in workflow files
6. Set job timeouts — prevent hung builds from burning minutes
7. Use path filters — skip CI for doc-only changes
8. Fail fast — run the quickest checks first to give fast feedback

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| No dependency caching | Builds take 2-5x longer than needed |
| Running everything sequentially | Independent jobs should run in parallel |
| Secrets in workflow files | Visible in logs and PR comments |
| No timeout on jobs | Hung jobs burn CI minutes indefinitely |
| Deploying on every push | Risky — use manual triggers or branch protection |
| Ignoring flaky tests | Flaky tests erode trust in the pipeline |

## Expected output

1. **Workflow file** — `.github/workflows/ci.yml` or equivalent
2. **Pipeline stages** — lint, test, build, deploy with clear dependencies
3. **Caching config** — dependencies and build artifacts cached
4. **Secret references** — documented secrets needed for deployment
5. **Optimization notes** — parallel jobs, path filters, timeouts configured
