---
name: figma-layout-reference
description: Create a layout reference document for a screen before or during Figma Console MCP work. Use when the user wants a Markdown spec of a screen's structure, frame hierarchy, auto layout, naming, components, or an ASCII layout diagram to guide building or QA in Figma.
---

# Figma Layout Reference

Produce a Markdown reference that a designer or an agent can follow when building or checking a screen in Figma with Console MCP.

## When to use
- The user asks for a layout, structure, or spec of a screen.
- The user is about to build, rebuild, or audit a screen with Figma Console MCP.
- The user asks for an ASCII layout, frame tree, or naming convention.

## Workflow

1. **Inventory the screen.** List every visible region, text block, control, and image, top to bottom and left to right. Mark each as fixed, fill, or hug.
2. **Build the ASCII layout.** Draw the screen with box characters, one box per region. Keep the grid aligned, and label controls in brackets (for example `[Send >]`). Check that every row has the same width.
3. **Define the frame tree.** Use a table with columns: level, frame name, layout type, size or constraint, notes. Root frame first, then columns, then components.
4. **Specify auto layout.** For each frame, state direction (vertical or horizontal), gap, padding, alignment, and whether it fills or hugs its container.
5. **Name layers.** Use slash-separated paths (`Home/Main/Input/Prompt`) so Console MCP operations can target them. Keep names stable and numbered where repeated (`Chip-01`).
6. **List components and variants.** Note default, hover, disabled, and faded states. Mark any text or color that should come from a style or variable.
7. **Add a QA checklist.** Include sidebar width, centering, shared max width, spacing tokens, text levels, and color variables.
8. **Close with hierarchy.** Rank headings, titles, body text, and captions from largest to smallest.

## Output format
Return a single Markdown document with these sections in order:
1. ASCII layout
2. Frame structure table
3. Region-by-region breakdown
4. Naming convention
5. Components and variants
6. QA checklist
7. Visual hierarchy

## Rules
- Mark estimated sizes as estimates unless the user gives measurements.
- Do not invent content that is not visible in the source. Mark unknowns as `TBD`.
- Keep the ASCII diagram readable at 80 columns where possible.
- Use the user's own labels for regions and text.
- If the user asks for a file, save it as `.md` and send it.