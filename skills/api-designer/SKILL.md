---
name: api-designer
description: Design REST and GraphQL APIs with proper resource modeling, endpoint structure, and OpenAPI specifications. Use when the user asks to design, plan, or create an API.
---

# API Designer

## Purpose

Design well-structured, consistent APIs with proper resource modeling, HTTP semantics, error handling, and documentation-ready specifications. Produces OpenAPI/Swagger specs or GraphQL schemas.

## When to use

- User says "design an API" or "create API endpoints"
- User needs to define resource models and relationships
- User wants an OpenAPI/Swagger specification
- User is planning a new service or microservice
- User asks to review or improve existing API design

## Workflow

### Step 1: Understand the domain

- Identify the core resources (nouns become resources)
- Map relationships between resources (1:1, 1:many, many:many)
- Clarify authentication and authorization requirements
- Ask about rate limiting, pagination, and versioning strategy

### Step 2: Model resources

- Define resource schemas with field types and constraints
- Use consistent naming: plural nouns, kebab-case for URLs
- Design nested relationships carefully (avoid deep nesting)
- Define standard query parameters: `?page=`, `?limit=`, `?sort=`, `?filter=`

### Step 3: Design endpoints

- Map CRUD operations to HTTP methods: GET/POST/PUT/PATCH/DELETE
- Define request/response schemas for each endpoint
- Design consistent error responses with status codes and messages
- Plan authentication: API keys, JWT, OAuth2 per endpoint group

### Step 4: Specify

- Generate OpenAPI 3.1 spec (REST) or SDL schema (GraphQL)
- Include examples for every request and response
- Document edge cases and validation rules
- Add rate limit headers and pagination metadata

## Best practices

1. Resources are nouns (`/users`, `/orders`), actions are HTTP methods
2. Use plural nouns consistently — never mix `/user` and `/users`
3. Version via URL path (`/v1/users`) or headers, not both
4. Return proper HTTP status codes: 201 Created, 404 Not Found, 422 Unprocessable
5. Use consistent error format: `{ "error": { "code": "...", "message": "..." } }`
6. Support partial updates with PATCH, full replacement with PUT
7. Paginate list endpoints by default — never return unbounded lists
8. Use HATEOAS links for discoverability when appropriate
9. Document every endpoint with request/response examples

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Using verbs in URLs (`/getUsers`) | Resources are nouns; verbs are HTTP methods |
| Inconsistent naming (`/users`, `/userProfile`) | Pick one convention and stick to it |
| Returning different error formats per endpoint | Clients can't parse errors reliably |
| No pagination on list endpoints | Unbounded responses cause performance issues |
| Deep nesting (`/users/1/orders/2/items/3`) | Use flat URLs with query params for filtering |
| Exposing internal database IDs | Use UUIDs or slugs for public-facing IDs |
| Missing validation rules in spec | Clients don't know what's accepted |

## Expected output

1. **Resource model** — schemas with field types, constraints, relationships
2. **Endpoint list** — full URL, method, parameters, request/response schemas
3. **OpenAPI/Swagger spec** — machine-readable, importable into tools
4. **Error format** — consistent error response structure
5. **Examples** — working request/response pairs for every endpoint
