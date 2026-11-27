---
name: figma-flatten-layers
description: "Flatten deeply nested Figma layers (5+ levels from the page root) that are pure passthrough wrappers with no styling or behavior. Use for /figma-flatten-layers or requests to unwrap nested groups."
---

# /figma-flatten-layers - Flatten Deep Nesting

Supports `preview`: show intended changes without applying.

## Scope

Use `get_selection`. If empty, use `get_page_nodes`. Never full-file without confirmation.

## Target

Nodes at depth ≥ 5 from page root (page = depth 0, direct child = depth 1). Use recursive `get_node_children` to build the tree and compute depth.

## Passthrough Definition

A node is a passthrough wrapper when `get_node_properties` shows all of:
- No `fills` (empty array or all invisible).
- No `strokes`.
- No `effects`.
- `cornerRadius = 0`.
- `clipsContent = false`.
- `layoutMode = NONE`.
- Constraints are default (`MIN` / `MIN`).
- No blend mode override (`blendMode = PASS_THROUGH`).
- `type ≠ COMPONENT` and `type ≠ INSTANCE`.

## Procedure

1. Record the full subtree structure via `get_node_children` before any writes.
2. Walk each passthrough chain. Collect the children of the deepest passthrough.
3. Use `move_node` to reparent each child to the nearest meaningful ancestor (first non-passthrough node up the chain).
4. After moving, verify z-order: compare `index` values. Re-order with `reorder_node` if needed.
5. After moving, re-read child `constraints` via `get_node_properties`. If the new parent frame differs in size, flag the child for constraint review.
6. Call `delete_node` on the now-empty passthrough wrappers.
7. Flag nodes where `type = INSTANCE` or `COMPONENT` — do not flatten into or through them.

## Output

For each flattened structure, show before/after as indented tree:

```
Before: Frame A > Group B > Group C > Text
After:  Frame A > Text
```

Prefix `[preview]` in preview mode — make no writes.

Summary: `N wrappers removed | deepest path was X levels | N constraint changes flagged | N ambiguous flagged`
