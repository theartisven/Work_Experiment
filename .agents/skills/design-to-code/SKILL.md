---
name: "design-to-code"
description: "Converts a Figma design into standalone HTML as accurately as possible. Use when the user asks to turn a Figma frame, screen, or component into code, or mentions Figma Agent, Figma MCP, or Figma Console MCP."
---

# Figma to Code

## Goal
Make the HTML match the Figma design as closely as possible: layout, spacing, sizes, colors, typography, layer order, and structure.

## Persona
Act as a developer who builds from Figma designs every day. Think in components, auto layout, and design tokens. Ask before guessing when the design is ambiguous.

## Input
Use whichever Figma tool is connected: Figma Agent, Figma MCP, or Figma Console MCP.

## Output format
- One standalone `.html` file.
- CSS is inline in a `<style>` block in the `<head>`. No external frameworks or build step.
- Design tokens go in CSS custom properties on `:root`.

## Procedure

### 1. Inventory the layers
Read the selected frame tree. List every layer with its type, size, position, and visibility.

### 2. Remove hidden layers
Drop layers where `visible = false`. Note their names in the summary so the user can confirm nothing important was dropped.

### 3. Map auto layout
- Auto layout frame → `display: flex` (or `grid` for wrapping rows and columns).
- Map direction, gap, padding, main-axis and cross-axis alignment, and wrap.
- If a frame has no auto layout, infer a flex layout from child positions and sizes. Flag each inferred frame in the summary so the user can check it.

### 4. Set z-order
- In Figma, the layer at the top of the list is in front.
- Convert to DOM order: later siblings paint on top.
- Add `z-index` only when elements overlap and DOM order is not enough.

### 5. Name by semantic HTML
- Choose the tag from the layer name and role: `header`, `nav`, `main`, `section`, `article`, `footer`, `button`, `ul`/`li`, `img`, `h1`–`h6`, `p`.
- Fall back to `div` with a BEM-style class when no tag fits.
- Keep the original layer name in a class or comment so it can be traced back.

### 6. Use tokens, or exact values
- If the file has variables or styles, map each value to a CSS custom property on `:root` and reference it by name.
- If a value has no token, use the exact px value from Figma.
- Keep font family, weight, size, line height, and letter spacing.

### 7. Handle assets
- Export images and icons as files (SVG for vectors) and reference them with relative paths.
- Do not rebuild vector shapes by hand.

### 8. Extract components
- Find repeated layers with the same structure (for example, cards or list rows).
- Write each one once as a reusable pattern in the HTML, such as a `<template>` element, and reuse it.
- List every extracted component in the summary.

### 9. Verify with a screenshot
- Render the HTML at the same size as the Figma frame.
- Compare it with a screenshot of the frame.
- Report any visual differences in the final message, with their locations. Do not change the HTML to fix them.

## Output
- The HTML file.
- A short summary covering:
  - hidden layers removed
  - frames where a flex layout was inferred
  - tokens used and values left as px
  - assets exported
  - components extracted
  - visual differences from the screenshot comparison

## Rules
- Never invent values that are not in the design.
- Flag anything you could not map instead of guessing.