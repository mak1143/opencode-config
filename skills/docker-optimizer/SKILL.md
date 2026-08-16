---
name: docker-optimizer
description: Create and optimize Dockerfiles and docker-compose configurations for security, size, and build speed. Use when the user asks to create, optimize, or debug Docker configurations.
---

# Docker Optimizer

## Purpose

Write production-ready Dockerfiles that are secure, minimal, and fast to build. Optimize image size, build caching, and security posture. Fix broken or inefficient Docker configurations.

## When to use

- User asks to create or write a Dockerfile
- User wants to optimize an existing Docker image (reduce size, speed up builds)
- User reports Docker build failures or cache invalidation issues
- User needs docker-compose configuration for multi-service setups
- User asks about Docker security best practices

## Workflow

### Step 1: Understand the application

- Identify the language, framework, and runtime requirements
- Check for existing Dockerfile, docker-compose, .dockerignore
- Understand the deployment target (local dev, staging, production)
- Identify services that need to communicate (databases, caches, queues)

### Step 2: Choose the base image

- Prefer slim/alpine variants (`python:3.12-slim`, `node:22-alpine`)
- Use specific tags, not `latest`
- Use multi-stage builds for compiled languages or complex build steps
- Match the base image to the production environment

### Step 3: Optimize the Dockerfile

- Order instructions from least to most frequently changing
- Copy dependency files first, install, then copy source code
- Use `--no-cache-dir` for pip, `--no-install-recommends` for apt
- Combine RUN commands to reduce layers
- Use `.dockerignore` to exclude unnecessary files

### Step 4: Secure the image

- Run as non-root user (`USER appuser`)
- Don't store secrets in environment variables (use Docker secrets)
- Scan for vulnerabilities (`docker scout`, `trivy`)
- Don't install unnecessary packages or development tools
- Use read-only filesystem where possible

### Step 5: Verify

- Build with `--no-cache` to test clean builds
- Check image size (`docker images`)
- Verify the application runs correctly in the container
- Test the build cache by rebuilding after a small change

## Best practices

1. Multi-stage builds: build stage for dependencies, final stage for runtime
2. Copy `requirements.txt` / `package.json` before source code for better caching
3. Use `.dockerignore` — exclude `.git`, `__pycache__`, `node_modules`, `venv`
4. Pin base image versions: `python:3.12.4-slim`, not `python:latest`
5. One process per container — don't bundle unrelated services
6. Use `HEALTHCHECK` instruction for orchestrator integration
7. Set `WORKDIR` before `COPY` to avoid absolute paths
8. Use `COPY` over `ADD` unless you need tar extraction

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Using `latest` tag | Builds are non-reproducible |
| Running as root | Security risk if container is compromised |
| Copying entire directory before installing deps | Cache invalidates on every code change |
| No .dockerignore | Bloated image, slower builds, leaked secrets |
| Multiple `RUN` commands without `&&` | Extra layers increase image size |
| Installing dev dependencies in production image | Larger attack surface, wasted space |
| Storing secrets in ENV | Visible in `docker inspect` and image history |

## Expected output

1. **Dockerfile** — optimized, multi-stage, non-root, with health check
2. **.dockerignore** — excludes unnecessary files
3. **docker-compose.yml** — if multi-service, with proper networking and volumes
4. **Image size report** — before/after optimization comparison
5. **Security notes** — non-root user, secret handling, vulnerability scan results
