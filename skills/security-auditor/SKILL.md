---
name: security-auditor
description: Audit code for security vulnerabilities, OWASP Top 10 issues, secret exposure, dependency risks, and license compliance. Use when the user asks to check security, audit code, review for vulnerabilities, or check dependencies.
---

# Security Auditor

## Purpose

Identify and report security vulnerabilities in code, configuration, and dependencies. Covers OWASP Top 10, secret scanning, dependency CVEs, and license compliance. Focus on actionable findings with clear remediation steps.

## When to use

- User says "check for security issues" or "audit this code"
- User wants to review input validation, authentication, or authorization
- User asks to scan for hardcoded secrets or credentials
- User needs OWASP Top 10 compliance check
- User wants to audit dependencies for known CVEs or outdated packages
- User asks about license compliance or dependency risks

## Workflow

### Step 1: Scope the audit

- Identify the attack surface: endpoints, inputs, file operations, database queries
- Check for authentication/authorization mechanisms
- Identify external dependencies and services
- Review configuration files for sensitive values

### Step 2: Scan for code vulnerabilities

- Check for SQL injection (string formatting in queries)
- Check for XSS (unsanitized output in templates/HTML)
- Check for CSRF (missing tokens on state-changing endpoints)
- Check for command injection (unsanitized input in shell commands)
- Check for path traversal (unsanitized file paths)
- Check for hardcoded secrets (API keys, passwords, tokens)

### Step 3: Audit dependencies

- Inventory all direct and transitive dependencies
- Run dependency audit (`pip-audit`, `npm audit`, `cargo audit`)
- Check for known CVEs in current versions
- Identify outdated packages with security patches
- Check for typosquatting or suspicious packages
- Check for unmaintained or abandoned packages

### Step 4: Check licenses

- Verify license compatibility with your project
- Flag GPL/AGPL in proprietary projects
- Check for license changes in new versions

### Step 5: Report

- Prioritize findings by severity (Critical → High → Medium → Low)
- Provide the exact file and line for each finding
- Suggest a fix for each vulnerability
- Note what's NOT a vulnerability (avoid false positives)

## Best practices

1. Focus on the OWASP Top 10 — most common web vulnerabilities
2. Check for least-privilege violations — does the code access more than needed?
3. Verify that auth checks exist on every protected endpoint
4. Run dependency audits in CI — catch vulnerabilities before deployment
5. Pin dependency versions and use lock files

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Only scanning for secrets | Misses injection, XSS, CSRF, and other OWASP issues |
| Ignoring transitive dependencies | Vulnerabilities hide in dependency trees |
| False positive overload | Real vulnerabilities get buried in noise |
| Ignoring configuration files | Secrets leak through env vars, config files, docker-compose |
| Not checking dependency CVEs | Vulnerable dependencies are the #1 attack vector |
| Skipping auth checks | Every endpoint needs explicit authorization verification |
| Trusting client-side validation | Server must validate everything — client validation is UX only |
| Ignoring license changes | Legal risk for commercial projects |

## Expected output

1. **Vulnerability list** — severity, file:line, description, fix
2. **Secret scan results** — any hardcoded credentials found
3. **Dependency audit** — CVEs, outdated packages, risk level
4. **License audit** — compatibility check for all dependencies
5. **OWASP checklist** — which Top 10 categories are addressed
6. **Remediation plan** — ordered by severity, with code examples
