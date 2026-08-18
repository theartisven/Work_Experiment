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

---

## PERMANENT RULES

**Before generating any screen, ask:**
- What is the screen size? Use `DESKTOP_RULE`, `TABLET_RULE`, or `MOBILE_RULE`.
- Light mode or dark mode?
- Wireframe or mockup?

**Before creating any component or style, check if it already exists in the file.**

**Always use Auto Layout when creating or editing screens and elements.** Align to the most common design pattern.

**Use only multiples of 8 for spacing and padding (8, 16, 24, 32).** No odd or random values.

**Apply a grid or column layout to every screen frame before placing content.**

**Add a description to every component** explaining its purpose and when to use it.

**Assess task complexity first.** If complex, break it into segments and present the breakdown. After each segment, ask the user to continue or enable auto mode.

**After creating a screen, always provide:**
- `{Frame Name}`
- `https://www.figma.com/design/{fileKey}?node-id={nodeId-with-dashes}`

> To build the URL: take `fileKey` from the current working file. Take `nodeId` from the MCP response (e.g. `123:456`). Replace `:` with `-` → `123-456`.

**When a brand logo or icon appears in an element,** fetch it from `https://thesvg.org/`.

**All x and y positions for frames and elements must be whole numbers only.**

**For text layers, never set a fixed width or height** — use Hug or Fill only.

**Name layers using semantic naming, following BEM conventions as reference.**

---

## TEMPORARY RULES

**When the user asks to create any animation, do not use Figma Motion.**