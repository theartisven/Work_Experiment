---
name: figma-autolayout
description: "Apply Figma auto layout to stack-like frames and groups that lack it, and normalize inconsistent padding and gaps in frames that already have it. Use for /figma-autolayout or requests to add auto layout or make frame spacing consistent."
---

# /figma-autolayout - Apply Auto Layout

Supports `preview`: show intended changes without applying.

## Scope

Use `get_selection` to get selected nodes. If empty, use `get_page_nodes` for the current page. Never operate on the full file without user confirmation.

## Stack Detection

Call `get_node_children` for each frame or group. A node qualifies as a stack when:
- All children share one primary axis (check `x` and `y` of each child).
- Gaps between children are consistent within ±2px (compute from child `x`/`y` and `width`/`height`).
- No children overlap (bounding boxes do not intersect).

Skip nodes that fail. Flag them with `annotate_node` or in output.

## Procedure

For each qualifying node:

1. Read current properties with `get_node_properties`: position, size, children layout.
2. Record originals before writing (store `layoutMode`, `itemSpacing`, `paddingTop`, `paddingRight`, `paddingBottom`, `paddingLeft`).
3. Call `set_layout_mode` with direction `HORIZONTAL` or `VERTICAL`.
4. Set `itemSpacing` to observed gap, snapped: `v < 16 ? round(v/4)*4 : round(v/8)*8`.
5. Set `primaryAxisAlignItems` and `counterAxisAlignItems` to match visual arrangement.
6. Set `layoutSizingHorizontal` / `layoutSizingVertical`:
   - `HUG` when frame sizes to children.
   - `FILL` when frame is full-width inside parent.
   - `FIXED` otherwise — flag for review.
7. For wrapping rows: set `layoutWrap = WRAP`, set `counterAxisSpacing` separately.
8. Skip nodes where `type = INSTANCE` or `type = COMPONENT`. Flag each.

For nodes that already have `layoutMode` set: normalize `itemSpacing` and padding to snapped values.

## Output

One line per changed node:

`frame name | direction | gap | resizing`

Prefix `[preview]` in preview mode — make no writes.

Summary: `N frames laid out | N values normalized | N instances skipped | N flagged`
