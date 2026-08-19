---
name: rules-generate
description:
original-author: sven hero kaufmann
contributor:
   - theodore galve
version: 1.6
---
### OTHER FILES TO USE WHEN GENERATING
- `01_project-context/rules-thinking.md` — Thinking and reasoning rules for the AI.
- `01_project-context/project-settings.md` — This file stores project variables, like the repeat value. Use it to check the current settings.

---```markdown
# ALWAYS

## Before You Start

**Ask the user before starting:**
- Screen size: `DESKTOP_RULE`, `TABLET_RULE`, or `MOBILE_RULE`?
- Theme: Light or dark mode?
- Design fidelity: Wireframe, LO-FI Mockup, or HI-FI Mockup?

**Check `DESIGN_LIBRARIES` first:**
- If all required components exist, proceed.
- If components are missing, create two versions based on existing design patterns. Ask the user to select one version before continuing.

---

## Layout and Spacing

**Use Auto Layout:**
- Apply Auto Layout to every screen and element that you create or edit.

**Forms:**
- Generate related or grouped fields with the same visual appearance.
- Avoid generic field labels.

**Components:**
- After using a component, check that it works correctly.
- If a component is broken, reset it before continuing.

**Spacing and padding:**
- Use multiples of 8 only.
- Allowed values include 8, 16, 24, and 32.
- Do not use other values.

**Grid and columns:**
- Add a grid or column layout to every screen frame before adding content.

**Positioning:**
- Use whole numbers for all X and Y positions.

**Text layers:**
- Do not set fixed width or height.
- Use `Hug` or `Fill` instead.

---

## Patterns and Generation

**Design patterns:**
- Always use the most common design pattern for the requested task.

**Images and video:**
- Always use `Fit`.

**Interactive elements:**
- Include the following states when applicable:
  - Empty state
  - Error state
  - Failure state

---

## Naming and Documentation

**Layer names:**
- Use semantic names.
- Use BEM naming as a reference.
- No "-" or "_"

**Component descriptions:**
- Add a description to every component.
- Explain:
  - The purpose of the component.
  - When to use the component.

---

## Complex Tasks

**Assess complexity before starting:**
- If the task is simple, proceed directly.
- If the task is complex:
  1. Divide the task into smaller segments.
  2. Show the task breakdown.
  3. Complete one segment at a time.
  4. After each segment, ask the user whether to continue or enable auto mode.

---

## After Every Screen

Apply these requirements after creating or editing each screen.

**Frame name:**
- Use the exact name shown in the Figma Layers panel:
  `{exactly-as-it-appears-in-layers}`

**Figma link:**
- Provide a clickable link using this format:
  `https://www.figma.com/design/{fileKey}?node-id={nodeId-converted}`

**Build the Figma link:**
1. Get `fileKey` from the current Figma file URL.
2. Get `nodeId` from the MCP response.
3. Example node ID: `123:456`
4. Replace `:` with `-`.
5. Example converted node ID: `123-456`.
6. Use the converted node ID in the Figma URL.
7. Format the URL as a clickable Markdown link.

**Components and nested groups:**
- If there is no top-level frame, link directly to the component or nested group node.
- Do not link to a parent frame.

---

## USE FOR NOW

**Animation:**
- Do not use Figma Motion when the user asks to create an animation.
```
