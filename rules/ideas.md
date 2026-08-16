---
alwaysApply: true
---

# Ideas — Brainstorm, Evaluate, Decide

## Brainstorming — diverge before converging

When asked to generate ideas, solutions, or approaches:

1. **Generate 3–5 options** before picking one — never jump to the first answer
2. **Diverge first** — quantity over quality in the first pass
3. **Converge second** — evaluate, eliminate weak options, refine strong ones
4. **Present tradeoffs** — never pretend one option is perfect

### Brainstorm format

```
Option A: [name]
  Pros: ...
  Cons: ...
  Effort: [low/medium/high]

Option B: [name]
  Pros: ...
  Cons: ...
  Effort: [low/medium/high]

Recommendation: [which one and why]
```

## Idea capture — structured recording

When the user shares an idea or you identify one during work, capture it:

```markdown
## Idea: [short title]

**Problem:** What pain point does this solve?
**Audience:** Who benefits?
**Solution:** One-paragraph description
**Tech:** Key technologies involved
**Scope:** [MVP / full feature / experiment]
**Effort:** [hours / days / weeks]
**Status:** [brainstorm / ready / in-progress / parked]
```

Store captured ideas in:
- `memory/ideas.md` for personal/project ideas
- `projects/<name>/memory.md` for project-specific ideas
- `commands/` if the idea is a repeatable workflow

## Project ideas — structured exploration

When user says "I have an idea" or "what if we built X":

1. **Clarify the problem** — what's broken or missing today?
2. **Identify the audience** — who exactly needs this?
3. **Scope it** — what's the smallest version that's useful?
4. **Tech landscape** — what existing tools/libraries could help?
5. **Risks** — what could make this fail?

### Exploration template

```
Problem: [one sentence]
Who cares: [target user/audience]
MVP: [smallest useful version]
Tech: [likely stack]
Risks: [top 2-3 failure modes]
Time: [honest estimate]
```

## Decision framework — structured tradeoffs

When choosing between approaches, use a decision matrix:

### Step 1: Define criteria

List what matters (performance, cost, maintainability, speed to ship, etc.)

### Step 2: Weight criteria

Rate importance 1–5 (5 = must have, 1 = nice to have)

### Step 3: Score options

Rate each option against each criterion (1–5)

### Step 4: Calculate

```
Option A: (criteria × weight) + (criteria × weight) + ... = total
Option B: (criteria × weight) + (criteria × weight) + ... = total
```

### Decision matrix example

```
Choose: Database for new project

| Criterion       | Weight | PostgreSQL | MongoDB | SQLite |
|-----------------|--------|------------|---------|--------|
| Relationships   | 5      | 5          | 2       | 4      |
| Scalability     | 4      | 4          | 5       | 2      |
| Setup ease      | 3      | 3          | 4       | 5      |
| Type safety     | 4      | 4          | 2       | 3      |
| Hosting cost    | 2      | 3          | 4       | 5      |
|-----------------|--------|------------|---------|--------|
| Total           |        | 78         | 65      | 62     |

Winner: PostgreSQL
```

## Tradeoff framing

Always present tradeoffs as explicitly:

- "Option A is faster but harder to maintain"
- "Option B ships quicker but won't scale past 10k users"
- "Option C is the safe choice but you'll revisit this in 6 months"

Never say "this is the best" without context. Say "best **for this constraint**."

## Feasibility check — before committing

Before recommending an idea to implement:

1. **Tech feasibility** — can this actually be built with available tools?
2. **Time estimate** — honest assessment, include unknowns
3. **Skill match** — does the team/user have the skills?
4. **Dependencies** — what external services, APIs, or libraries are required?
5. **Reversibility** — how hard is it to undo if it doesn't work?

If feasibility is low, say so: "This is possible but [reason]. Consider [simpler alternative] first."

## Idea refinement — stress-test the idea

When reviewing or refining an idea:

- **Challenge assumptions** — "Is it true that users need X?"
- **Ask the failure question** — "What would make this fail?"
- **Flip it** — "What if we did the opposite?"
- **Time-box it** — "What could we build in 2 hours vs 2 weeks?"
- **Scope pressure** — "What if we cut 50% of features — is it still useful?"

Never rubber-stamp an idea. Push on it until it's either stronger or replaced by something better.
