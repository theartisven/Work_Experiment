# AGENTS

This folder contains guides that help AI tools, such as GitHub Copilot, do different tasks. This is not an application. There is nothing to build or run. There are no tests to run.

> **Access notation:**
> - `None` = no access
> - `Limited` = partial access
> - `RO` = read-only
> - `RW` = read and write
> - `RO / RW (user)` = read-only; write needs user permission

> **User notation:**
> - `User` = the human owner
> - `Agent` = the AI tool
> - `User and Agent` = both share this

## Folder Structure

| Name | User | Access | Purpose |
|---|---|---|---|
| `.agents/` | Agent | Limited | Holds agent guides, skills, references, and project structure files. |
| `.others/` | User | None | Holds the user's private notes. |
| `.vscode/` | User and Agent | RO / RW (user) | Holds local VS Code and MCP configuration. |
| `created/` | Agent | RW | Holds files created by the agent. |
| `in progress/` | User and Agent | RO / RW (user) | Holds work that is being developed or refined. |
| `resources/` | User | None | Holds tools and files needed for use. |

### Agent Folder Guides

| Name | User | Access | Purpose |
|---|---|---|---|
| `.agents/references/` | Agent | RO | Reference guides for tools and workflows. |
| `.agents/skills/` | Agent | RO | Task-specific guides for design, text, and workflow operations. |
| `.agents/structure/` | Agent | RO / RW (user) | Files on how to set up project rules, settings, and memory. |

### Reference Guides

| Name | Agent | Access | Purpose | Scope |
|---|---|---|---|---|
| `mcp/FIGMA.MD` | Agent | RO | Explains Console-first tool selection and MCP fallbacks. | Figma |

### Structure Guides

| Name | User | Access | Purpose | Scope |
|---|---|---|---|---|
| `generate` | Agent | RO / RW (user) | Makes designs with the project rules. | Design, Figma |
| `instruction` | Agent | RO / RW (user) | Gives the agent basic rules to do work carefully. | General |
| `memory` | Agent | RW | Builds and updates a memory bank from conversations or documents. | General |
| `project-settings` | User and Agent | RO / RW (user) | Stores shared settings for design work. | Design, Figma |

### Skills Guides

| Name | User | Access | Purpose | Scope |
|---|---|---|---|---|
| `ASD-STE100` | Agent | RO | Rewrites technical text with ASD-STE100 Simplified Technical English rules. | Text, General |
| `Caveman` | Agent | RO | Makes answers shorter while preserving the important details. | General |
| `Desktop to Mobile` | Agent | RO | Creates a 390 px mobile version of a selected desktop Figma frame. | Figma |
| `Figma Accessibility` | Agent | RO | Checks Figma designs against WCAG AA accessibility criteria. | Figma |
| `Figma Auto Layout` | Agent | RO | Adds or normalizes Figma Auto Layout and frame spacing. | Figma |
| `Figma Consistency` | Agent | RO | Checks spacing, color, typography, components, and naming across Figma screens. | Figma |
| `Figma Grid` | Agent | RO | Aligns Figma values to an 8 pt grid. | Figma |
| `Figma Flatten Layers` | Agent | RO | Removes deeply nested passthrough Figma layers. | Figma |
| `Figma Remove Layers` | Agent | RO | Removes empty, duplicate, hidden, and unused Figma layers. | Figma |
| `Figma Rename` | Agent | RO | Renames Figma layers with BEM, HTML, or semantic conventions. | Figma |
| `Figma Run All` | Agent | RO | Runs grouped Figma layout, cleanup, or audit operations. | Figma |
| `Figma Spelling` | Agent | RO | Checks Figma text for spelling errors and wrong words. | Figma |
| `Figma to Code` | Agent | RO | Converts a Figma frame or screen into standalone HTML. | Figma, Code |
| `Figma Whitespace` | Agent | RO | Normalizes spacing and removes spacer layers in Figma. | Figma |
| `Humanizer` | Agent | RO | Rewrites text to reduce common AI-style phrasing. | Text, General |
| `I Have ADHD` | Agent | RO | Organizes answers with clear next steps and less distraction. | General |