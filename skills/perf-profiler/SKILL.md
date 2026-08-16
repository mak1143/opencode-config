---
name: perf-profiler
description: Profile and optimize Python application performance — identify bottlenecks, reduce latency, improve throughput. Use when the user asks to make code faster, profile performance, or optimize resource usage.
---

# Performance Profiler

## Purpose

Systematically identify and fix performance bottlenecks. Measure before optimizing — never guess about what's slow. Every optimization must be backed by profiling data.

## When to use

- User says "this is slow" or "optimize this"
- User needs to reduce response time, memory usage, or CPU load
- User asks to profile a specific function, endpoint, or workflow
- User reports performance regression after a change
- User needs to handle increased load or data volume

## Workflow

### Step 1: Establish baseline

- Measure current performance (response time, memory, CPU)
- Define what "fast enough" means — set a target
- Identify the performance bottleneck type: CPU-bound, I/O-bound, memory-bound
- Check if there's a profiling tool already configured

### Step 2: Profile

- Use `cProfile` for CPU-bound code (function call counts and timing)
- Use `memory_profiler` for memory usage
- Use `py-spy` for production profiling without code changes
- Use `line_profiler` for line-by-line analysis of hot functions
- Profile with realistic data volumes — not toy examples

### Step 3: Analyze

- Identify the top 3 slowest operations (Pareto: 80/20 rule)
- Determine if the bottleneck is algorithmic, I/O, or resource contention
- Check for N+1 queries, unnecessary serialization, redundant computations
- Check for memory leaks or excessive allocation

### Step 4: Optimize

- Fix the biggest bottleneck first — measure after each change
- Common fixes: caching, batching, lazy evaluation, connection pooling
- Don't optimize code that isn't the bottleneck
- Verify correctness after optimization — speed shouldn't break behavior

## Best practices

1. Measure first, optimize second — never guess about what's slow
2. Optimize the biggest bottleneck first — diminishing returns are real
3. Use realistic data sizes and traffic patterns for profiling
4. Profile in production-like conditions — dev environments lie
5. Cache expensive computations with `functools.lru_cache` or Redis
6. Batch database queries — N+1 is the most common performance killer
7. Use async I/O for concurrent network requests
8. Set performance budgets and enforce them in CI

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Optimizing without profiling | You might optimize the wrong thing |
| Micro-optimizing non-hot code | Wasted effort on code that runs once |
| Optimizing before measuring baseline | No way to prove improvement |
| Ignoring I/O bottlenecks | Most web apps are I/O-bound, not CPU-bound |
| Adding cache without invalidation strategy | Stale data bugs are harder to find than slow code |
| Breaking correctness for speed | A fast wrong answer is worse than a slow right one |

## Expected output

1. **Profile data** — cProfile output, memory profile, or timing measurements
2. **Bottleneck analysis** — top 3 slowest operations with data
3. **Optimizations applied** — specific changes with before/after measurements
4. **Performance report** — response time, memory, throughput before and after
5. **Tradeoff notes** — what was sacrificed (readability, complexity) for speed
