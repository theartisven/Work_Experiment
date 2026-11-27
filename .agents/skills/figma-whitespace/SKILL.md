---
name: figma-whitespace
description: "Normalize Figma whitespace: consistent snapped gaps between siblings, removal of spacer layers faking spacing, and trimmed text content. Use for /figma-whitespace or requests to fix uneven spacing."
---

# /figma-whitespace - Fix Whitespace

Supports `preview`: show intended changes without applying.

## Scope

Use `get_selection`. If empty, use `get_page_nodes`. Never full-file without confirmation.

## Intentional Irregularity

Skip a frame without changes when:
- Node name contains: `hero`, `feature`, `banner`, `custom`.
- An adjacent sticky or annotation node (check siblings via `get_node_children` on parent) contains the word `intentional`.

## Procedure

For each in-scope frame:

1. Record all `itemSpacing` and padding values via `get_node_properties` before writing.
2. **Gap normalization:** collect all `itemSpacing` values across siblings. Compute dominant value (most frequent). Snap all to `round8`. Write via `set_node_properties`.
3. **Spacer removal:** call `get_node_children`. For each child where `type = FRAME` or `type = RECTANGLE`, check: `width` or `height` = 0, no `fills`, no `strokes`, no `effects`, no children. If all true, it is a spacer. Delete via `delete_node`.
4. **Text trim:** for each child where `type = TEXT`, read `characters` via `get_node_properties`. If leading or trailing whitespace or `\n` exists, write trimmed value via `set_node_properties`. Leave internal spaces unchanged.
5. After spacer removal, re-read `itemSpacing` to verify gap is correct.

## Output

One line per changed frame:

`frame name | gaps changed | spacers removed | text trimmed`

Prefix `[preview]` in preview mode — make no writes.

Summary: `N gaps normalized | N spacers removed | N text layers trimmed | N frames flagged`
