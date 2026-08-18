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

---
# ALWAYS

## Before You Start

**Ask the user upfront:**
- Screen size: `DESKTOP_RULE`, `TABLET_RULE`, or `MOBILE_RULE`?
- Light or dark mode?
- Wireframe or mockup?

**Check your DESIGN_LIBRARIES first.**
- All components exist? Proceed.
- Missing components? Generate two versions based on existing patterns, then let the user pick.

---

## Layout & Spacing

**Use Auto Layout** on every screen and element you create or edit.

**Spacing & padding:** Only multiples of 8. (8, 16, 24, 32—no odd numbers.)

**Grid or column layout** on every screen frame before placing content.

**X and Y positions:** Whole numbers only.

**Text layers:** Never fix width/height. Use Hug or Fill only.

---

## Patterns & Generation

**Always create the most common design pattern** for the task.

**Images & video:** Always use fit.

**Interactable elements:** Include empty states, error handling, and failure cases.

---

## Naming & Documentation

**Layer names:** Semantic naming, using BEM as reference.

**Component descriptions:** Add one to every component explaining its purpose and when to use it.

---

## Complex Work

**Assess task complexity first.** If complex, break it into segments and show the breakdown. After each, ask the user to continue or enable auto mode.

---

## External Assets

**Brand logos or icons:** Fetch from `https://thesvg.org/`.

---

## After Every Screen (Create or Edit)

**Frame Name:** `{exactly-as-it-appears-in-layers}`

**Figma Link:** `https://www.figma.com/design/{fileKey}?node-id={nodeId-converted}`

**Building the link:**
- `fileKey` from your current file URL
- `nodeId` from MCP response (e.g., `123:456`)
- Replace `:` with `-` → `123-456`
- Format as markdown so it's clickable

**For components or nested groups** (no top-level frame): Link to the node directly, not a parent.

---

## USE FOR NOW

**When the user asks to create any animation, do not use Figma Motion.**