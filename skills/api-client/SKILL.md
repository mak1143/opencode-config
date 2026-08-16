---
name: api-client
description: Consume external APIs — handle authentication, retries, pagination, error handling, and rate limiting. Use when the user asks to call an API, integrate with a service, or build an API client.
---

# API Client

## Purpose

Build reliable API clients that handle authentication, retries, pagination, error handling, and rate limiting. Focuses on consuming APIs, not designing them (see `api-designer` for that).

## When to use

- User says "call this API" or "integrate with [service]"
- User needs to authenticate with an API (OAuth2, API keys, JWT)
- User asks to handle pagination, retries, or rate limits
- User wants to build a reusable client wrapper
- User reports API integration issues (timeouts, 429s, auth failures)

## Workflow

### Step 1: Understand the API

- Read the API documentation (use Context7 MCP if available)
- Identify authentication method: API key, OAuth2, JWT, Basic Auth
- Understand rate limits, pagination format, and error response structure
- Check for SDK/client libraries that already exist

### Step 2: Design the client

- Choose: use existing SDK, HTTP library (httpx, requests), or raw HTTP
- Define the authentication mechanism and token refresh strategy
- Plan retry logic: which errors retry, how many times, backoff strategy
- Handle pagination: cursor-based, offset-based, or link-header

### Step 3: Implement

- Set timeouts on all requests (connect + read)
- Implement retry with exponential backoff for 5xx and 429
- Handle rate limits: read `Retry-After` header, respect limits
- Parse error responses consistently — raise meaningful exceptions
- Log requests and responses for debugging (without logging secrets)

### Step 4: Verify

- Test with valid credentials and expected responses
- Test error paths: 401, 403, 404, 429, 500
- Test retry behavior: simulate transient failures
- Test pagination: verify all pages are consumed

## Best practices

1. Use existing SDKs when available — don't reinvent the client
2. Set timeouts on every request — never wait indefinitely
3. Implement retry with exponential backoff — not immediate retry
4. Handle rate limits proactively — read `Retry-After` headers
5. Don't log secrets — mask API keys and tokens in logs
6. Use connection pooling for high-throughput clients
7. Validate responses against the expected schema
8. Build for idempotency — retries shouldn't create duplicate resources

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| No timeout on requests | Hangs indefinitely on unresponsive servers |
| Immediate retry on failure | Amplifies load on struggling servers |
| Ignoring rate limits | Gets your API key banned |
| Logging API keys | Secret exposure in logs |
| Hardcoding credentials | Can't rotate keys without code changes |
| Not handling pagination | Only gets the first page of results |
| Catching all exceptions | Masks real errors that should propagate |

## Expected output

1. **Client code** — reusable, with auth, retries, and error handling
2. **Configuration** — credentials stored securely, not hardcoded
3. **Error handling** — meaningful exceptions for each failure mode
4. **Retry policy** — documented backoff strategy and max retries
5. **Test results** — valid, error, and retry scenarios verified
