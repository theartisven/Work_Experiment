---
name: general-rules
description:
author: sven hero kaufmann
version: 1.0
---

## RULES

1. When the user asks to generate a screen, ask these questions first:
   - What is the screen size? Use the value from `DESKTOP_RULE`, `TABLET_RULE`, or `MOBILE_RULE`.
   - Light mode or dark mode?
   - Wireframe or mockup?

2. Always check if a component or style exists in the file before creating a new one.

3. When creating a new screen or element, always use Auto Layout. For text layers, never set a fixed width or height — only use Hug or Fill.

4. Always set spacing and padding using multiples of 8 (8, 16, 24, 32). Never use odd or random values.

5. Always use a grid or column layout on every screen frame before placing content.

6. Always add a description or note to every component explaining its purpose and when to use it.

7. Always assess the complexity of the task. If the task is too complex, break it down into segments. Present the breakdown to the user. After completing each segment, ask the user to continue to the next segment or enable auto mode.