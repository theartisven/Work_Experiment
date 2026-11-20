---
name: "figma-cleanup"
description: "Clean up Figma layers: remove unused/empty layers, flatten deep nesting, rename layers (BEM/HTML/simple modes)."

dateCreated: 2026-11-05T09:42:16+08:00
dateUpdated: 2026-11-05T10:06:31+08:00
hasBasicImage: false
basicImage: 
---
 

# /figma-cleanup - Figma Layer Cleanup

 

## Commands

- `/figma-cleanup help` → print command list
- `/figma-cleanup` (no arg) → run all: remove → flatten → rename (bem mode)
- `/figma-cleanup remove` → remove useless layers only
- `/figma-cleanup flatten` → flatten deep nesting only
- `/figma-cleanup rename [mode]` → rename layers only. Mode: `bem` (default), `html`, `simple`
- Any command + `preview` → show intended changes without applying

## Remove Useless Layers

Delete/flag for deletion:

- Empty groups/frames with zero children
- Frames/groups with exactly one child and no styling (no fill, stroke, radius, effect, padding)
- Duplicate layers stacked identically with same properties
- Dead layers: visibility toggled off. Flag each with name + parent; ask user to confirm deletion
DO NOT delete anything with fills, text content, effects, or component instances - flag instead.
 

## Flatten Deep Nesting

For groups/frames nested 5+ levels deep with no styling at intermediate levels (pure passthrough wrappers):

- Collapse/unwrap intermediate levels so children attach to nearest meaningful ancestor
- Preserve levels adding real behavior (auto layout, clipping, effects, constraints, component boundaries)
- Flag ambiguous structures instead of guessing

## Rename Layers

 

### Mode: `bem` (Default)

`block__element--modifier` format:

- block = containing component/section (e.g., `card`, `nav`)
- element = child part (e.g., `card__title`)
- modifier = state/variant (e.g., `button--primary`)
- lowercase, hyphen-separated, no spaces/camelCase
Repeated blocks (4+ instances): `card-001`, `card-002`, etc.
Repeated blocks (2-3 instances): `card-top`, `card-middle`, `card-bottom`
 

### Mode: `html`

Semantic HTML roles (accessibility-focused):

- Structural: `header`, `nav`, `main`, `footer`, `section`, `article`, `aside`
- Interactive: `button`, `link`, `input-text`, `input-checkbox`, `select`
- Text: `h1`–`h6`, `p`, `label`, `caption`
- Lists: `list`, `list-item`
- Media: `img`, `figure`, `figcaption`
Nested frames as hyphenated compounds: `nav-link`, `card-heading`, `form-input-email`
 

### Mode: `simple`

Plain descriptive names:

- Lowercase, space-or-hyphen separated: `profile picture`, `submit button`
- Describe what it is and what it's for: `error message` not just `text`
- No BEM syntax, no forced semantic tags

## Output

Report: layers removed (with names), dead layers flagged, levels flattened, layers renamed (old → new). Flag content-bearing nodes not deleted, ambiguous naming, ambiguous flatten targets.
