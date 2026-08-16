---
name: start-file
description:
author: sven hero kaufmann
version: 1.0
---

## When to Start a Chat

1. Create `.project-context/project-variables.md`.
2. The AI uses this file for general project context.
3. If this file does not exist, ask the user for these variables one at a time:

### FIGMA_RULE
What rules should the Figma MCP use?
(Open text input for user to describe custom Figma rules)

### DESKTOP_RULE
Which desktop screen size?
- `1920` — Windows Desktop
- `1440` — Apple Desktop
- `custom` — Enter a custom width

### TABLET_RULE
Which tablet screen size?
- `800` — Android tablet
- `768` — iPad tablet
- `custom` — Enter a custom width

### MOBILE_RULE
Which mobile screen size?
- `360` — Android phone
- `375` — Apple iPhone
- `custom` — Enter a custom width

## Other Files

- `general-rules.md` — The AI reads this file to know how to act.