---
name: figma-consistency
description: "Read-only cross-screen consistency check across multiple selected Figma frames. Finds inconsistent spacing, color, typography, component usage, and naming across screens. Requires 2 or more frames selected. Supports token and freestyle modes. Use for /figma-consistency or requests to check consistency across screens or flows."
---

# /figma-consistency - Cross-Screen Consistency Checker

Read-only. Make zero writes.

## Mode

Two modes. Default is `freestyle`.

- `/figma-consistency` or `/figma-consistency freestyle` — **Freestyle mode.** Values are compared against each other across frames. Flags when the same semantic element uses different raw values. Ignore variables, text styles, color styles, and effect styles completely. Do not bind, resolve, or report any style or variable metadata.
- `/figma-consistency token` — **Token mode.** Values are compared against the file's Figma variables and local styles. Flags when a value is used without a bound variable, or when two frames use different tokens for the same semantic element. Requires the file to have variables (`get_local_variables`) or styles (`get_local_styles`). If neither exist, reply: `No variables or styles found. Use freestyle mode instead.`

The mode changes how color, spacing, and typography checks resolve values — see each check below.

## Scope

Call `get_selection`. If fewer than 2 nodes are selected, stop and reply: `Select 2 or more frames to compare.`

Skip outer artboard frames (`width` ∈ `{390, 768, 1440, 1920}`) as containers — but still check their children via `get_node_children`.

## Data Collection

For each selected frame, call `get_node_children` recursively. Build a flat map per frame:

```
{ nodeId, name, type, x, y, width, height, fills, strokes,
  fontSize, fontWeight, fontFamily, lineHeight,
  paddingTop, paddingBottom, paddingLeft, paddingRight,
  itemSpacing, cornerRadius, layoutMode, componentId,
  boundVariables, fillStyleId }
```

Read all via `get_node_properties` per node. Use `componentId` to identify component instances.

**Freestyle mode:** do not read or collect `boundVariables`, `fillStyleId`, `textStyleId`, `effectStyleId`, paint styles, text styles, or effect styles. Do not call style or variable lookup APIs. The flat map is raw geometry and property values only.

**Token mode only:** add `textStyleId` and `effectStyleId` to the flat data as needed, call `get_local_variables` and `get_local_styles` once at the start. Build lookup maps:
- `variableMap`: `{ id → { name, resolvedValue } }`
- `styleMap`: `{ id → { name, type } }`

## Checks

Run across all frames together.

### Spacing Consistency

**Freestyle:** collect only raw `itemSpacing` and `paddingTop/Right/Bottom/Left` values. Ignore variable bindings and spacing variables. Compute dominant value per property. Flag nodes where value differs from dominant by more than 4px and does not match `round8`.
Format: `frame | layer | property | value | expected`

**Token:** for each spacing value, check `boundVariables` for a matching spacing variable. Flag when no variable is bound. Flag when two frames bind the same semantic element to different spacing variables.
Format: `frame | layer | property | value | bound variable (or none)`

### Color Consistency

**Freestyle:** collect only raw `fills` hex values. Ignore variable bindings, color variables, text styles, color styles, and `fillStyleId`. Do not bind or resolve fill styles. Flag fills that appear on only one frame and flag when the same semantic role (matched by `name`) uses different hex values across frames.
Format: `frame | layer | color found | expected`

**Token:** for each fill, check `fillStyleId` against `styleMap` and `boundVariables` against `variableMap`. Flag when neither is bound. Flag when two frames use different style IDs or variable IDs for the same semantic element.
Format: `frame | layer | color found | bound style/variable (or none) | expected`

### Typography Consistency

**Freestyle:** collect only raw `fontSize`, `fontWeight`, `fontFamily`, and `lineHeight` values per text node. Group by semantic role (match `name` to `h1`–`h6`, `p`, `label`). Flag when same role uses different raw values across frames. Ignore `textStyleId`, text styles, and font variables completely. Do not bind or report text style bindings in this mode.
Format: `frame | layer | property | value | expected`

**Token:** check `textStyleId` against `styleMap`. Flag text nodes with no bound text style. Flag when same semantic role binds to different text style IDs across frames.
Format: `frame | layer | property | value | bound style (or none) | expected`

### Component Consistency
Group nodes by `componentId`. Flag when:
- Same `componentId` has significantly different overrides across frames (check `characters`, `fills`, `visible` on children).
- A node with no `componentId` has the same `name` as one with a `componentId` on another frame (detached instance).
Format: `frame | layer | issue | recommendation`

### Naming Consistency
Group nodes by structural position (depth + index within parent). Flag when equivalent nodes across frames have different `name` values.
Format: `frame | layer name | equivalent on other frame | mismatch`

### Icon Consistency
Find nodes where `type = VECTOR` or `name` contains `icon`. Group by apparent function (match by `name` stem). Flag size or fill differences.
Format: `frame | layer | size or fill | expected`

## Priority

- **Critical** — same semantic element, different values, no apparent reason.
- **Warning** — unusual value, may be intentional.

## Output

First line: `Mode: freestyle` or `Mode: token`

One section per check with findings only:

`## [Check name] — N issues (X critical, Y warnings)`

One line per issue in that check's format.

If nothing found: `No consistency issues detected.`
