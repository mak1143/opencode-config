---
name: design-system
description: Build and maintain a design system with tokens, components, and patterns. Use when the user asks to create a design system, define tokens, build a component library, or establish visual consistency.
---

# Design System

## Purpose

Create a consistent, scalable design system with reusable tokens, components, and patterns. This skill handles the workflow of building design systems. For visual execution rules (color, typography, spacing), see `graphic-design.md`. For interface patterns (accessibility, responsive, feedback), see `ui-ux.md`.

## When to use

- User says "create a design system" or "define our design tokens"
- User needs consistent color, typography, and spacing across projects
- User wants to build a component library or pattern collection
- User asks to document existing design decisions
- User needs to standardize UI patterns across multiple pages/apps

## Workflow

### Step 1: Audit existing design

- Collect existing screenshots, style guides, and brand assets
- Identify current inconsistencies (colors, fonts, spacing)
- Catalog existing components and their variations
- Determine the design system's scope (one product or multi-product)

### Step 2: Define tokens

- **Color** — primary, secondary, accent, neutral, feedback (success, warning, error)
- **Typography** — type scale (h1-h6, body, caption), font families, line heights
- **Spacing** — base unit (4px or 8px), scale (4, 8, 12, 16, 24, 32, 48, 64)
- **Shadows** — elevation levels (sm, md, lg, xl)
- **Border radius** — small, medium, large, full
- **Breakpoints** — sm (640), md (768), lg (1024), xl (1280)

### Step 3: Define components

- List all components: button, input, card, modal, toast, etc.
- Define each component's variants (size, color, state)
- Specify props/API for each component
- Define interaction states: default, hover, focus, active, disabled

### Step 4: Document and implement

- Write usage guidelines per component
- Provide code examples for each variant
- Include do/don't examples
- Publish as a Storybook, documentation site, or token files

## Best practices

1. Start with tokens — they're the foundation everything else builds on
2. Use semantic tokens (`color-error`) over primitive tokens (`color-red-500`)
3. Keep the component API minimal — props should have clear purposes
4. Version the design system — breaking changes need migration guides
5. Build a Figma/design tool source of truth that mirrors the code

## Common mistakes

| Mistake | Why it's wrong |
|---|---|
| Starting with components before tokens | No foundation leads to inconsistency |
| Too many variants per component | Decision paralysis for consumers |
| Inconsistent naming | `btn` vs `button` vs `Button` confuses consumers |
| No versioning | Breaking changes have no migration path |
| Design system without adoption plan | Built but never used |

## Expected output

1. **Token definitions** — color, typography, spacing, shadows in code
2. **Component specs** — props, variants, states, accessibility requirements
3. **Usage guidelines** — do/don't examples per component
4. **Code examples** — implementation-ready snippets
5. **Token files** — CSS variables, JSON tokens, or theme config
