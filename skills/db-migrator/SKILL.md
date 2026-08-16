---
name: db-migrator
description: Create, manage, and rollback database schema migrations using Alembic, Django, or raw SQL. Use when the user needs to change database structure, add tables/columns, or fix migration issues.
---

# Database Migrator

## Purpose

Safely evolve database schemas through versioned migrations with rollback support. Ensures data integrity during schema changes and provides a clear history of structural changes.

## When to use

- User says "add a column" or "create a new table"
- User needs to modify existing schema (rename, drop, change type)
- User asks to rollback a migration or fix a broken migration
- User wants to generate migrations from model changes
- User reports migration conflicts or dependency issues

## Workflow

### Step 1: Understand the current state

- Check existing migration history (`alembic history`, `showmigrations`)
- Read the current schema or model definitions
- Identify the migration tool in use (Alembic, Django, raw SQL)
- Check for pending migrations that haven't been applied

### Step 2: Design the migration

- Write the schema change as a reversible operation
- Plan for data migration if the change involves existing data
- Consider impact on running queries and active connections
- Decide: single migration or separate schema + data migrations

### Step 3: Generate the migration

- Use the tool's auto-generation when possible (`alembic revision --autogenerate`)
- Review the generated migration — never trust auto-generation blindly
- Add data migrations separately from schema changes when needed
- Include a downgrade path in every migration

### Step 4: Verify and apply

- Test the migration on a copy of production data (or staging)
- Verify the downgrade path works (`alembic downgrade -1`)
- Check for lock contention on large tables
- Apply during low-traffic windows for production

## Best practices

1. Every migration must have a working downgrade — no one-way doors
2. Separate schema changes from data migrations when possible
3. Never modify a migration that's already been applied to production
4. Add indexes CONCURRENTLY to avoid locking tables
5. Test migrations against realistic data volumes
6. Use `ALTER TABLE ... ADD COLUMN` with defaults to avoid full table rewrites
7. Keep migrations small — one logical change per migration
8. Name migrations descriptively: `add_user_email_index`, not `update_table`

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| No downgrade path | Can't undo a bad migration |
| Modifying applied migrations | Causes conflicts with other environments |
| Dropping a column used in queries | Runtime errors for active code |
| Auto-generated migration without review | May drop columns or lose data |
| Large data migrations in a single transaction | Locks the table for extended periods |
| Adding NOT NULL column without default | Fails on existing rows |
| Ignoring index lock behavior | Blocks reads/writes during index creation |

## Expected output

1. **Migration file** — versioned, reversible, with clear description
2. **Downgrade script** — tested path back to previous state
3. **Data migration** — if applicable, separate from schema change
4. **Impact notes** — tables affected, estimated lock time, index changes
5. **Verification steps** — how to confirm the migration applied correctly
