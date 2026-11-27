---
name: figma-a11y
description: "Read-only Figma accessibility assessment against WCAG AA: color contrast, text size, touch targets, color-only signaling, missing accessible names, focus states, and readability. Use for /figma-a11y or requests to check accessibility of a Figma design."
---

# /figma-a11y - Accessibility Assessment

Read-only. Make zero writes.

## Scope

Use `get_selection`. If empty, use `get_page_nodes`. Never full-file without confirmation.

## Data Collection

For each node, read via `get_node_properties`:
- `fills`, `strokes`, `effects` — for color and contrast.
- `fontSize`, `fontWeight`, `lineHeight`, `characters` — for text checks.
- `width`, `height` — for size checks.
- `reactions` — for interactive element detection.
- `visible`, `opacity` — skip invisible nodes.
- `name` — for accessible name check.

Detect base font size from most-used `fontSize` across body text nodes.

## Checks

Each line includes a fix suggestion as the last column.

**Color contrast** — WCAG 1.4.3
Compute luminance from `fills` RGB. Compare text luminance to background luminance.
Thresholds: 4.5:1 normal text, 3:1 for `fontSize ≥ 24` or (`fontSize ≥ 18` and `fontWeight ≥ 700`).
Skip nodes with `opacity < 1` on the disabled component variant — flag as exempt.
Format: `layer name | ratio found | required | fix suggestion`

**Text size** — WCAG 1.4.4
Flag `fontSize < (base - 2)` with floor at 10px.
Format: `layer name | size | issue | fix suggestion`

**Touch targets** — WCAG 2.5.5
Flag nodes with `reactions` non-empty where `width < 44` or `height < 44`.
Use outer frame bounds, not visible icon bounds.
Format: `layer name | hit area | visible size | fix suggestion`

**Color-only signaling** — WCAG 1.4.1
Flag text nodes where the only state difference between variants is `fills` color (no icon sibling, no underline, no shape change).
Format: `layer name | issue | fix suggestion`

**Missing accessible names** — WCAG 1.1.1
Flag `type = VECTOR` or `type = INSTANCE` (icon-like) nodes with no adjacent `type = TEXT` sibling and no `name` matching a semantic role.
Format: `layer name | issue | fix suggestion`

**Focus states** — WCAG 2.4.7
Flag nodes with `reactions` where no sibling variant has `name` containing `focus` or `:focus`.
Format: `layer name | issue | fix suggestion`

**Readability** — WCAG 1.4.8
For body text: flag `lineHeight < fontSize * 1.4`. Flag lines where `characters` length exceeds 75 chars (approximate from `width / fontSize * 1.6`).
Format: `layer name | value | issue | fix suggestion`

**Motion** — WCAG 2.3.3
Flag nodes whose `name` contains `animation`, `transition`, or `motion` with no sibling variant named `reduced-motion` or `prefers-reduced-motion`.
Format: `layer name | issue | fix suggestion`

## WCAG AA Summary

`## WCAG AA Summary`

One line per criterion with failures:
`1.4.3 Contrast: 4 failures`

## Output

Output only the check lists and the WCAG AA Summary. If nothing found: `No accessibility issues detected.`
