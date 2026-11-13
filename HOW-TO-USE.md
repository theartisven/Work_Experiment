## How to Start
_Last Update: 2026-11-13 version 3_

Install these tools before you begin:

- Install Visual Studio Code.
- Install the Figma Extension in VS Code.
- Install Figma Desktop.
- (Optional) Get a Pro Figma Account.
  > NOTE: A free account works. Some features are not available on the free plan.

---

## Setup

### Part 1 — Figma MCP

- Open `.mcp.json`.
- Find the `url` field.
- Set the correct address:
  - Local (VS Code + Co): `http://127.0.0.1:3845/mcp`
  - Remote MCP (pilot): `https://mcp.figma.com/mcp`
- Click Start above the `figma-mcp` property.

---

### Part 2 — Figma Console

**A — Create a Personal Access Token**

- Open Figma.
- Go to User Settings. Go to Security.
- Find the Personal Access Tokens section.
- Click Create.
- Enter a name. Example: `Figma-Console`.
- Set an expiration time.
- Select your scopes.
  > NOTE: If you are not sure, select all checkboxes in User, Files, and Design Systems.
- Click Generate.
- Copy the token.

**B — Add the token to your project**

- Duplicate `.env-sample`.
- Rename the duplicate to `.env`.
- Replace `your_figma_token_here` with the token.

**C — Connect Figma Desktop**

- Open Figma Desktop.
- Open the file you are working on.
- Go to Figma Logo > Plugin > Development > Import plugin from manifest.
- Select `manifest.json` in `_needed/figma-desktop-bridge`.
- Select Figma Desktop Bridge in plugins.
- Click Connect.

**D — Enable in MCP config**

- Open `.mcp.json`.
- Click Start above the `figma-console` property.

---

### Part 3 — Last Part

**A — Project Settings**

- Go to `.agents/structure/project-settings/SKILL.md`.
- Find `FIGMA_URL:`.
- Add the project Figma URL.

**B — Read Agents.md**

- Open `AGENTS.md`.
- Read it for a short overview of the files included.
