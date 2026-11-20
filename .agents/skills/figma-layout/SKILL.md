---
name: "figma-layout"
description: "Fix Figma layout geometry: auto layout, 8pt grid snapping, and whitespace normalization."

dateCreated: 2026-11-05T09:42:16+08:00
dateUpdated: 2026-11-05T10:06:31+08:00
hasBasicImage: false
basicImage: 
---
 

# /figma-layout - Figma Layout Fixer

 

## Commands

- `/figma-layout help` → print command list
- `/figma-layout` (no arg) → run all: autolayout → grid → whitespace
- `/figma-layout autolayout` → apply auto layout only
- `/figma-layout grid` → snap to 8pt grid only
- `/figma-layout whitespace` → fix whitespace only
- Any command + `preview` → show intended changes without applying

## Fix Auto Layout

For every frame/group behaving like a stack (children aligned in row/column with consistent gaps) but lacking auto layout:

- Apply auto layout (direction = row or column, matching visual arrangement)
- Set gap = observed spacing, snapped per Grid rules
- Set resizing: hug contents unless frame is full-width (then fill container)
Normalize inconsistent padding/gap in frames that already have auto layout.
 

## Snap to 8pt Grid

Applies to: padding (all 4 sides), corner radius, font size, gap/spacing, x, y, width, height.

 

Rule: round to nearest multiple of 8, EXCEPT allow multiples of 4 for values under 16.

```
round8(v) = v<16 ? round(v/4)*4 : round(v/8)*8
```

Font size: prefer nearest value from type scale (12,14,16,18,20,24,28,32,40,48) over raw round8.

 

Width/height: skip aspect-ratio-locked assets; flag instead.

 

x/y: if node is inside auto-layout frame, skip manual x/y; instead ensure frame's own x/y and item spacing are snapped.

 

## Fix Whitespace

- Normalize gap/spacing between siblings to consistent, snapped (8pt/4pt) amounts
- Remove stray empty text nodes or spacer layers faking spacing (use auto layout gap/padding instead)
- Trim leading/trailing whitespace inside text layer content
- Flag (don't change) intentionally irregular spacing (e.g., asymmetric hero sections)

## Output

Report: counts of frames auto-layouted, values snapped, whitespace fixed. Flag aspect-locked assets, ambiguous cases for user confirmation.
