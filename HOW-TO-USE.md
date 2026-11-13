## How to Start
_Last Update: 2026-11-13 version 3_

Install these tools before you begin:

- Install Visual Studio Code.
- Install the Figma Extension in VS Code.
- Install Figma Desktop.
- (Optional) Get a Pro Figma Account.
  > NOTE: A free account works. Some features are not available on the free plan.

---
## To Do List

> 🔧 Fix · ➕ Add · 🧪 Experiment

| | Category | Item |
|---|---|---|
| 🔧 | To Fix | Memory skill |
| 🔧 | To Fix | MCP connection error |
| ➕ | To Add | Adding persona |
| ➕ | To Add | Adding figma skills |
| 🧪 | To Experiment | Adding other MCP |

---
## Setup
>Note:
> - mcp.json is Global
> - .mcp.json is Local < What we are using

### Part 1 — Figma MCP

- Open `.mcp.json`.
- Find the `url` field.
- Set the correct address:
  - Local (VS Code + Co-Pilot): `http://127.0.0.1:3845/mcp`
  - Remote MCP (pilot): `https://mcp.figma.com/mcp`
- Click Start above the `figma-mcp` property.

---

### Part 2 — Figma Console

**A — Create a Personal Access Token**
- Duplicate `.env-sample`.
- Rename the duplicate file to `.env`.

- Open Figma (Any) > Settings > Security.
- Find the Personal Access Tokens section and click Create.
- Enter a name (Any) and set an expiration time.
- Select your scopes.
  > NOTE: If you are not sure, select all checkboxes in User, Files, and Design Systems.
- Click Generate.
- Copy the token.

- in `.env`, replace `your_figma_token_here`  with the token.

**B — Connect Figma Desktop**

- Open Figma Desktop.
- Open the file you are working on.
- Go to Figma Logo > Plugin > Development > Import plugin from manifest.
- Select `manifest.json` in `_needed/figma-desktop-bridge`.
- Select `Figma Desktop Bridge` in plugins.
- Click Connect.

**C — Enable in MCP config**

- Go to `.vscode/mcp.json`.
- Click Start above the `figma-console` property.

---

### Part 3 — Last Part

**A — Project Settings**

- Go to `.agents` folder
- Go to `structure/project-settings/SKILL.md`.
- Find `FIGMA_URL:`.
- Add the project Figma URL.

**B — Read Agents.md**

- Open `AGENTS.md` markdown.
- Read it for a short overview of the files included.
