---
name: figma-rename-semantic
description: "Rename Figma layers using semantic HTML roles for accessibility (header, nav, button, h1, img, and so on). Use for /figma-rename-semantic or requests to rename layers with semantic HTML naming."
---

# /figma-rename-semantic - Rename Layers (Semantic HTML)

Supports `preview`: show intended renames without applying.

## Scope

Use `get_selection`. If empty, use `get_page_nodes`. Never full-file without confirmation.

**Always skip (do not rename):**
- `type = INSTANCE` or `COMPONENT` — check via `get_node_properties`.
- Frames where `width` ∈ `{390, 768, 1440, 1920}` — artboard containers, not semantic elements.

## Protected Names

Skip a node whose current `name` exactly matches a role-vocabulary term or a hyphenated compound of two terms (see vocabulary below). Mark as `protected` in output.

## Role Vocabulary

Assign the role that best matches the node's visual and structural purpose:

| Role | When to use |
|---|---|
| `header` | Top section with branding or nav |
| `nav` | Navigation container |
| `main` | Primary content area |
| `footer` | Bottom section |
| `section` | Thematic grouping within a page |
| `article` | Self-contained content (post, card) |
| `aside` | Secondary or sidebar content |
| `button` | Tappable action element |
| `link` | Text or element navigating elsewhere |
| `input-text` | Single-line text input |
| `input-checkbox` | Checkbox input |
| `select` | Dropdown selector |
| `h1`–`h6` | Heading by visual size/weight |
| `p` | Body text paragraph |
| `label` | Form field label |
| `caption` | Small descriptive text |
| `list` | List container |
| `list-item` | Individual list row |
| `img` | Meaningful image |
| `img-decorative` | Decorative image with no meaning |
| `figure` | Image + caption container |
| `figcaption` | Caption within a figure |

Nested: use hyphenated compound — `nav-link`, `card-heading`, `form-input-email`.

## Role-Specific Rules

- **Conflict:** when a node fits two roles, prefer the interactive intent. Flag ambiguous cases.
- **card / list-item block:** children named `card-heading`, `card-body`, `card-footer`.
- **section vs article:** `article` for self-contained content; `section` for thematic grouping.
- **input + label:** after renaming, check each `input-*` node for a sibling or ancestor named `label`. Flag missing pairings.
- **Heading order:** after renaming, verify `h1`–`h6` sequence has no skipped levels in the frame. Flag violations.

## Record

Before any writes, collect all current `name` values via `get_node_properties`.

## Output

One line per renamed node:

`old name → new name`

Prefix `[preview]` in preview mode — make no writes.

Protected, skipped, and flagged nodes listed separately. Role count summary: `button: 4 | h1: 2 | ...`
