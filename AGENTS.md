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
| `.agents` | Agent | Limited | Holds agent guides, skills, and supporting files. |
| `.others` | User | None | Holds the user's private notes. |
| `_archive` | User | None | Stores unwanted files. |

### Agent Folder Guides

| Name | User | Access | Purpose |
|---|---|---|---|
| `.agents/created/` | Agent | RW | The agent puts the files it makes here. |
| `.agents/persona/` | Agent | RO | When the user asks the agent to pretend to be someone else, the agent can use these files to get references. |
| `.agents/references/` | Agent | RO | Reference guides for tools and workflows. |
| `.agents/skills/` | Agent | RO | When the user asks for a specific task, the agent can use these files to get references. |
| `.agents/structure/` | Agent | RO / RW (user) | Files on how to set up project rules, settings, and memory. |

### Reference Guides

| Name | Agent | Access | Purpose | Scope |
|---|---|---|---|---|
| `mcp/FIGMA.MD` | Agent | RO | Explains Console-first tool selection and MCP fallbacks. | Figma |
| `user-interface/` | Agent | RO | Guidelines references for interface design. | User interface |

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
| `ASD-STE100` | Agent | RO | Rewrites technical text in simpler English with ASD-STE100 rules. | Text, General |
| `Caveman` | Agent | RO | Makes answers much shorter and keeps the important details. | General |
| `Humanizer` | Agent | RO | Edits text to sound more natural and less like AI text. | Text, General |
| `I Have ADHD` | Agent | RO | Organizes answers with clear next steps and less distraction. | General |