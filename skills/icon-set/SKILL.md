---
name: icon-set
description: Create consistent SVG icon sets with naming conventions, size grids, and stroke standards. Use when the user asks to create icons, build an icon library, or design a set of UI icons.
---

# Icon Set

## Purpose

Create a cohesive set of SVG icons with consistent visual properties: stroke width, size grid, corner radius, and naming conventions. Icons should work at multiple sizes and feel like they belong to the same family.

## When to use

- User says "create icons" or "design an icon set"
- User needs a set of UI icons for a project (navigation, actions, status)
- User wants to standardize existing icons
- User needs icons in specific sizes or formats
- User asks to name and organize an icon library

## Workflow

### Step 1: Define the grid

- Choose a base size: 24x24px (standard), 20x20, or 16x16
- Define the stroke width: 1.5px (default), 2px (bold), 1px (light)
- Set corner radius: 0 (sharp), 1px (subtle), 2px (rounded)
- Define padding within the grid: 2px minimum padding

### Step 2: Plan the set

- List all icons needed by category (navigation, actions, status, objects)
- Identify visual metaphors for abstract concepts
- Group icons by complexity — simple, medium, detailed
- Prioritize: which icons are needed first?

### Step 3: Design

- Draw each icon on the defined grid
- Maintain consistent visual weight across all icons
- Use simple geometric shapes — avoid unnecessary detail
- Test at target sizes — does the icon read clearly at 16px?
- Ensure optical alignment, not mathematical centering

### Step 4: Implement and organize

- Export as SVG with clean markup (no unnecessary attributes)
- Use consistent naming: `icon-name` or `icon-name-variant`
- Organize by category in a clear directory structure
- Provide an index or manifest for programmatic access

## Best practices

1. Use a fixed grid (24x24) and stick to it for all icons
2. Keep stroke width consistent — 1.5px is the sweet spot for most UIs
3. Limit detail — icons must read at 16px
4. Use consistent corner radius across all icons
5. Name icons by function, not appearance (`icon-search`, not `icon-magnifying-glass`)
6. Provide light/dark variants if needed
7. Use `currentColor` for stroke color — lets icons inherit text color
8. Keep SVG markup clean — remove metadata, comments, and editor attributes

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Inconsistent stroke width | Icons look like they're from different families |
| Too much detail | Icons become unreadable at small sizes |
| Inconsistent naming | `edit`, `pencil`, `pen` for similar concepts |
| Different visual weight | Some icons look heavier/lighter than others |
| No padding in grid | Icons touch the edges, look cramped |
| Using fill instead of stroke | Style inconsistency with stroke-based icons |

## Expected output

1. **SVG files** — clean, optimized, consistent markup
2. **Naming convention** — documented, consistent naming scheme
3. **Size variants** — 16px, 20px, 24px, 32px if needed
4. **Icon manifest** — JSON or index listing all icons with metadata
5. **Usage guide** — how to use, size, and color the icons
