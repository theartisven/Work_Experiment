---
name:
description:
---

# Memory bank

Append entries by span in this format: `- [RULE] [span] content`.

## Facts

- [extract-facts] [turn 2] The memory bank must auto-update after every 3 user messages.
- [extract-facts] [turn 1] The project-settings skill currently uses desktop width 1440 px, tablet width 768 px, and mobile width 390 px.
- [extract-facts] [turn 1] The default Figma page is “🏀 Playground [General]”.

## Entities

## Episodes

- [summarize-episode] [turn 1] The project settings and workspace guide were updated to match the current Figma page, viewport widths, folder structure, and installed skill inventory.

## Changes

- [detect-change] [turn 1] The project-settings skill changed from version 1.7 to version 1.8, and the Figma file URL moved out of the skill while the default page, desktop, tablet, and mobile values remained active project settings.
- [detect-change] [turn 1] AGENTS.md changed from a partial workspace and skill inventory to an updated inventory that includes .vscode, in progress, resources, structure guides, and all currently available Figma and text skills.

## Goals

- Goal (ongoing): Keep AGENTS.md, project settings, and the memory bank synchronized with the current workspace and project configuration.
- Goal (ongoing): Check and update the memory bank automatically after every 3 user messages.
