---
name: cache-strategy
description: Design and implement caching strategies — invalidation patterns, TTL, Redis, CDN, and application-level caching. Use when the user asks to add caching, improve performance with cache, or fix cache-related bugs.
---

# Cache Strategy

## Purpose

Design effective caching with clear invalidation strategies. Caching solves performance problems but introduces consistency challenges. Every cache needs a plan for when data goes stale.

## When to use

- User says "add caching" or "cache this"
- User needs to reduce database load or API calls
- User reports stale data or cache invalidation issues
- User asks about Redis, Memcached, or CDN caching
- User wants to implement application-level caching (LRU, TTL)

## Workflow

### Step 1: Identify what to cache

- Profile to find the expensive operations (database queries, API calls, computations)
- Determine read/write ratio — cache reads, not frequent writes
- Identify data freshness requirements — how stale is acceptable?
- Check if a cache layer already exists (Redis, CDN, app-level)

### Step 2: Choose the caching layer

- **In-process** (`functools.lru_cache`) — fastest, single-process only
- **Redis/Memcached** — shared across processes, network latency
- **CDN** — static assets, API responses with public URLs
- **Database** — query result cache, materialized views
- **Browser** — HTTP cache headers (Cache-Control, ETag)

### Step 3: Design invalidation

- **TTL-based** — expires after N seconds (simple, eventual consistency)
- **Event-based** — invalidates on write (strong consistency, more complex)
- **Version-based** — cache key includes version hash (atomic updates)
- **Write-through** — cache updates with database (consistent, slower writes)
- **Write-behind** — cache updates asynchronously (fast writes, risk of data loss)

### Step 4: Implement and verify

- Set appropriate TTL based on freshness requirements
- Implement cache warming for cold-start scenarios
- Test cache hit, miss, and invalidation paths
- Monitor cache hit ratio — below 80% means the cache isn't effective

## Best practices

1. Cache the result, not the computation — cache after the expensive work
2. Always set TTL — unbounded cache is a memory leak
3. Handle cache miss gracefully — fall back to the source
4. Use cache keys that include all influencing parameters
5. Monitor hit ratio — low hit ratio means wrong data is cached
6. Implement cache warming for critical paths
7. Consider stampede protection — locks or lazy regeneration
8. Document invalidation strategy — future you will forget

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Caching without invalidation plan | Stale data served forever |
| No TTL on cache entries | Memory grows unbounded |
| Caching frequent writes | Cache is always stale, adds overhead |
| Ignoring cache stampede | Thundering herd on cache expiry |
| Caching at the wrong layer | In-process cache doesn't help other servers |
| Not monitoring hit ratio | Can't tell if cache is helping |

## Expected output

1. **Caching layer** — chosen and configured (Redis, LRU, CDN)
2. **Invalidation strategy** — TTL, event-based, or version-based
3. **Cache key design** — documented naming convention
4. **Hit ratio baseline** — measured before and after implementation
5. **Edge cases** — cache miss, stampede, cold start handled
