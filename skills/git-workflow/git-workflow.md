# GIT-WORKFLOW.md — fhirms

## Learning & Collaboration Agreement

- **Command Mastery First:** Every terminal command provided in responses must be accompanied by an explicit explanation of _what_ it does, _why_ it is necessary, and _how_ it prevents conflicts.
- **Active Memory Checks:** When recurring Git scenarios occur (e.g., branch cleanup, staging, syncing main), prompt the developer to recall or explain the commands rather than blindly pasting them.

---

## Branches

- **`main`** — Default/production branch. Always deployable. Prep files live here[cite: 6].
- **`feature/NN-section-name`** — One feature branch per section build (e.g., `feature/02-hero`, `feature/cta`, `feature/works-layout`)[cite: 6].

---

## Push & PR Policy

- **Prep & Prompts:** Direct push to `main` or quick PR[cite: 6].
- **Codebase (`index.html`, components, styles):** Always via PR[cite: 6].
- **Upstream Tracking (`-u` vs standard push):**
  - `git push -u origin <branch>`: Use **ONLY ONCE** on the initial push of a new feature branch to establish upstream tracking.
  - `git push origin <branch>`: Use for all subsequent commits on that branch.

---

## Standard Feature Branch Lifecycle

### 1. Pre-Branch Sync (Prevent Outdated Base Conflicts)

Always pull the latest `main` before branching[cite: 1, 3]:

```bash
git checkout main
git pull origin main
git checkout -b feature/NN-section-name
```
