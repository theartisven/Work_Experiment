---
name: figma-remove-layers
description: "Remove useless Figma layers: empty groups, unstyled single-child wrappers, duplicate stacked layers, and hidden dead layers. Use for /figma-remove-layers or requests to delete unused or empty layers."
---

# /figma-remove-layers - Remove Useless Layers

Supports `preview`: show intended changes without applying.

## Scope

Use `get_selection`. If empty, use `get_page_nodes`. Never full-file without confirmation.

## Pre-delete Reference Check

Before deleting any node, check via `get_node_properties`:
- `componentPropertyReferences` is non-empty → flag, do not delete.
- `reactions` is non-empty → flag, do not delete (prototype link).
- `boundVariables` is non-empty → flag, do not delete.

## Delete Targets

Only delete nodes that pass the reference check.

**Empty containers:** `get_node_children` returns 0 children and node `type = FRAME` or `GROUP`.

**Passthrough wrappers:** exactly 1 child, and node has no `fills`, no `strokes`, no `effects`, `cornerRadius = 0`, no `paddingTop/Right/Bottom/Left`, no `layoutMode`, no `clipsContent`.

**Exact duplicates:** compare siblings by `x`, `y`, `width`, `height`, and `fills`. When two match exactly, keep topmost (`index` lower = higher in stack), delete the rest.

**Off-canvas:** node `x + width < 0` or `y + height < 0` or `x > page width` or `y > page height`. Flag before deleting — confirm with user.

## Flag, Do Not Delete

- `visible = false` nodes: flag with name, full path, parent name. Ask user to confirm before deleting.
- Nodes with `fills`, `characters`, `effects`, or `type = INSTANCE` or `COMPONENT`.
- Any node that failed the reference check.

## Deletion Record

Before calling `delete_node`, record: name, full path, `type`, `fills`, `width`, `height`.

## Output

One line per deleted node:

`full path | reason | type | size`

Preview: prefix each line `[would delete]` or `[would flag]`. Make no changes.

Summary: `N deleted | N flagged (hidden) | N skipped (referenced) | N skipped (content)`
