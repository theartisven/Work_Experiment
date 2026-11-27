---
name: figma-grid
description: "Snap Figma padding, corner radius, font size, spacing, x, y, width, and height to an 8pt grid. Use for /figma-grid or requests to snap or align values to the 8pt grid."
---

# /figma-grid - Snap to 8pt Grid

Supports `preview`: show intended changes without applying.

## Scope

Use `get_selection`. If empty, use `get_page_nodes`. Never full-file without confirmation.

## Properties to Snap

Read each node with `get_node_properties`. Snap these fields:

| Property | API field |
|---|---|
| Padding | `paddingTop`, `paddingRight`, `paddingBottom`, `paddingLeft` |
| Corner radius | `cornerRadius`, `topLeftRadius`, `topRightRadius`, `bottomLeftRadius`, `bottomRightRadius` |
| Font size | `fontSize` |
| Gap | `itemSpacing`, `counterAxisSpacing` |
| Position | `x`, `y` |
| Size | `width`, `height` |

Do **not** snap: `strokeWeight`, shadow `blur`, shadow `spread`.

## Rounding Rule

```
round8(v) = v < 16 ? round(v / 4) * 4 : round(v / 8) * 8
```

Ties: round up. Property overrides:
- `fontSize`: use nearest from `[12,14,16,18,20,24,28,32,40,48]` — ignore round8.
- `width`/`height`: skip if node has `constrainProportions = true`. Flag it.
- `x`/`y`: skip if parent has `layoutMode` set. Snap parent's `x`/`y` and `itemSpacing` instead.

## Conflict Rule

When two sibling nodes would snap to the same value from different originals, flag both — do not apply.

## Post-snap Check

After writing, call `get_node_properties` again. If `width` or `height` changed and a text node now overflows (`textAutoResize` changed state), flag the node.

## Token Binding

If file has variables, call `get_local_variables`. When a snapped value matches a variable within 0px, bind via `set_bound_variable` instead of writing a raw number.

## Output

One line per changed value:

`layer name | property | old → new`

Prefix `[preview]` in preview mode — make no writes.

Summary: `N values snapped | N tokens bound | avg snap distance Xpx | N flagged`
