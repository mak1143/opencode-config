---
description: Update completion percentages and keep tracking files in sync
---
Update completion progress from **verified evidence only** and keep the two
tracking files in sync.

## Evidence rubric
- **Phase build project completed and verified** — +1 to each skill that project
  used; +15% to its category bar (e.g. bento-grid done → CSS, JS +1; Frontend +15%)
- **In-session review confirming a new capability** (with `file:line` cited) — +1 to that skill
- **Milestone marked done in `session-to-session.md` and verified** — +1
- Cap: max +2 per skill per week
- No evidence → no change. Never accept user-declared numbers alone.

## Files
1. `memory/progress-tracking.md` — category bars (█ filled, ░ empty, 10 blocks
   per 100%). Frontend opens with a 20% baseline (HTML 7/10 grandfathered).
2. `memory/skill-tree.md` — per-skill levels. HTML 7/10 is the sole grandfathered
   baseline; everything else started at 0.
3. Update `lastUpdated` in both files.

`progress-tracking.md` is the user-facing summary; `skill-tree.md` is the
per-skill breakdown. Record the evidence with every change.
