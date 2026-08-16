---
alwaysApply: true
---

# Security — Protect the System and Its Secrets

## Secrets

- Never log, print, expose, or commit API keys, tokens, passwords, or private keys
- Scan diffs before staging; if a secret is found, stop and tell the user immediately
- Load secrets from env vars or a secret manager — never hardcode
- Tokens get least privilege and short expiry

## Input handling

- Validate all external input: type, length, range, and allowlists
- Never trust data from users, URLs, headers, or third parties
- Use parameterized queries — never interpolate strings into SQL
- Sanitize output for HTML, shell, and URLs to prevent injection

## Defense

- Apply least privilege: only the access the code actually needs
- Use secure defaults; fail closed on uncertain paths
- Follow OWASP Top 10 when auditing or building features
- Audit dependencies for known CVEs; pin versions; update regularly

## In doubt

- When unsure whether something is a vulnerability, treat it as one and escalate
- State the risk clearly with impact and a recommended fix
