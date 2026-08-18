---
name: initialization-file
description: Defines the project initialization workflow for creating project-variables.md, including checking for existing variables, collecting missing project configuration values one at a time, handling multi-country compliance modes, selecting design libraries, and confirming the collected configuration before creating the project variables file.
original-author: sven hero kaufmann
contributor:
   - theodore galve
version: 1.6
---
## When to Start a Chat

1. Create `00_project-context/project-variables.md`.
2. The AI uses this file for general project context.
3. Check if this file exists:

   * **If exists:** Read the file. Identify missing variables. Ask only about the missing ones.
   * **If does not exist:** Ask for all variables one at a time.

### Step 1: Ask FIGMA_RULE

"What rules should the Figma MCP use?"

(Open text input)

Wait for answer. Store value. Move to Step 2.

### Step 2: Ask DESKTOP_RULE

"Which desktop screen size?"

* `1920` — Windows Desktop
* `1440` — Apple Desktop
* `custom` — Enter a custom width

Wait for answer. Store value. Move to Step 3.

### Step 3: Ask TABLET_RULE

"Which tablet screen size?"

* `800` — Android tablet
* `768` — iPad tablet
* `custom` — Enter a custom width

Wait for answer. Store value. Move to Step 4.

### Step 4: Ask MOBILE_RULE

"Which mobile screen size?"

* `360` — Android phone
* `375` — Apple iPhone
* `custom` — Enter a custom width

Wait for answer. Store value. Move to Step 5.

### Step 5: Ask COUNTRY_RULE

"Which country or countries for this user?"

* `custom` — Enter country name(s)

(Accept single or multiple countries separated by commas. Example: "US, UK, Germany")

Wait for answer. If multiple countries are entered, move to Step 5b. If a single country is entered, store the value and move to Step 6.

### Step 5b: Ask Compliance Mode

"You selected multiple countries. Which approach for conflicting rules?"

**Overlap Mode:**

* Follow rules that apply to all countries or majority (>50%).
* Flag rules that don't overlap in a summary.
* Best for: global audiences where some regional rules can be waived.

**Strict Mode:**

* Follow all rules from every country.
* Prioritize the strictest requirement if rules conflict.
* Best for: legal/security-critical work where compliance is mandatory.

Wait for answer. Store value. Move to Step 6.

### Step 6: Ask DESIGN_LIBRARIES

"What is the name of the design library or design system to use?"

* `custom` — Enter design library name(s)

(Accept a single or multiple design library names separated by commas. Example: "Material Design, MUI, Internal Design System")

Wait for answer. Store value. Move to Confirm and Create section.

### Confirm and Create

Summarize all collected project variables and verify that they are complete and correct.

The confirmation must include:

* `FIGMA_RULE`
* `DESKTOP_RULE`
* `TABLET_RULE`
* `MOBILE_RULE`
* `COUNTRY_RULE`
* Compliance Mode, if multiple countries were selected
* `DESIGN_LIBRARIES`

Ask the user to confirm whether the collected configuration is correct.

- **If confirmed:** Create `00_project-context/project-variables.md`.
- **If corrections are requested:** Update only the affected values, then ask for confirmation again.
- **If variables are still missing:** Ask only for the missing variables before requesting confirmation again.

The generated `00_project-context/project-variables.md` file must use this exact front matter:

---
name: project-variables
description: Defines project-wide variables for Figma UI generation, including the reference Figma design system and component library, standard desktop, tablet, and mobile screen widths, and South Korea as the regional context for legal and UI considerations. These variables are used together with general-rules.md when generating screens and UI elements.
---

Do not modify, shorten, paraphrase, or otherwise alter this front matter.

The content after the front matter must follow the established variable format:

- Start with `## Project Variables`.
- Define each variable as its own `### VARIABLE_NAME` section.
- Use a consistent `**Field:** Value` format for variable values.
- Follow each variable with a clear instruction describing how the AI should use it.
- Separate variable sections with `---`.
- Do not include a `## How to Use These Variables` section.
- Preserve all collected values exactly as confirmed by the user.
- Do not remove, rename, or restructure existing variables unless explicitly instructed by the user.
- If additional variables are introduced in future steps, add them as new `### VARIABLE_NAME` sections using the same format.
- Additional variables must be added without changing the established front matter or the format of existing variables.

## Other Files

- `general-rules.md` — The AI reads this file to know how to act.