---
name: init-file

description: Defines the project initialization workflow for creating project-settingss.md, including checking for existing variables, collecting missing project configuration values one at a time, handling multi-country compliance modes, selecting design libraries, and confirming the collected configuration before creating the project variables file.
original-author: sven hero kaufmann
contributor:
   - theodore galve
version: 2.0
---
## When to Start a Chat

1. Create `00_project-context/project-settingss.md`.
2. The AI uses this file for general project context.
3. Check if this file exists:

   * **If exists:** Read the file. Identify missing variables. Ask only about the missing ones.
   * **If does not exist:** Ask for all variables one at a time.

# Step 1: Ask `FIGMA_URL`

**"What Figma should the MCP edit (use URL)?"**

(Open text input)

- If the user skips or submits an empty value, store `FIGMA_URL = ""`.
- Wait for answer.
- Store value.
- Move to Step 2.

# Step 2: Ask `DESKTOP_RULE`

**"Which desktop screen size?"**

- `1920` — Windows Desktop
- `1440` — Apple Desktop
- `custom` — Enter a custom width

- If the user skips or submits an empty value, store `DESKTOP_RULE = ""`.
- If `custom` is selected, ask for the custom width.
- If the custom width is skipped or empty, store `DESKTOP_RULE = ""`.
- Otherwise, store the custom width.
- Move to Step 3.

# Step 3: Ask `TABLET_RULE`

**"Which tablet screen size?"**

- `800` — Android tablet
- `768` — iPad tablet
- `custom` — Enter a custom width

- If the user skips or submits an empty value, store `TABLET_RULE = ""`.
- If `custom` is selected, ask for the custom width.
- If the custom width is skipped or empty, store `TABLET_RULE = ""`.
- Otherwise, store the custom width.
- Move to Step 4.

# Step 4: Ask `MOBILE_RULE`

**"Which mobile screen size?"**

- `360` — Android phone
- `375` — Apple iPhone
- `custom` — Enter a custom width

- If the user skips or submits an empty value, store `MOBILE_RULE = ""`.
- If `custom` is selected, ask for the custom width.
- If the custom width is skipped or empty, store `MOBILE_RULE = ""`.
- Otherwise, store the custom width.
- Move to Step 5.

# Step 5: Ask `COUNTRY_RULE`

**"Which country or countries for this user?"**

- `custom` — Enter country name(s)

Accept a single or multiple countries separated by commas.

Example:

`US, UK, Germany`

- If the user skips or submits an empty value, store `COUNTRY_RULE = ""` and move to Step 6.
- If a single country is entered, store the value and move to Step 6.
- If multiple countries are entered, move to Step 5b.

# Step 5b: Ask Compliance Mode

**"You selected multiple countries. Which approach for conflicting rules?"**

## Overlap Mode

- Follow rules that apply to all countries or the majority (`>50%`).
- Flag rules that don't overlap in a summary.
- Best for global audiences where some regional rules can be waived.

## Strict Mode

- Follow all rules from every country.
- Prioritize the strictest requirement if rules conflict.
- Best for legal/security-critical work where compliance is mandatory.

- If the user skips or submits an empty value, store `COMPLIANCE_MODE = ""`.
- Otherwise, store the selected mode.
- Move to Step 6.

# Step 6: Ask `DESIGN_LIBRARIES`

**"What is the name of the design library or design system to use?"**

- `custom` — Enter design library name(s)

Accept a single or multiple design library names separated by commas.

Example:

`Material Design, MUI, Internal Design System`

- If the user skips or submits an empty value, store `DESIGN_LIBRARIES = ""`.
- If `custom` is selected, ask for the design library name(s).
- If the custom input is skipped or empty, store `DESIGN_LIBRARIES = ""`.
- Otherwise, store the provided value.
- Move to **Confirm and Create**.

# Global Empty/Skip Rule

For **every step**:

- If the user skips the question, submits an empty value, or provides only whitespace, treat the value as empty.
- Store the corresponding variable as `""`.
- **Do not ask the same question again.**
- Continue to the next applicable step.
- **Do not apply a default value** unless the user explicitly selects it.
- For conditional steps such as **Step 5b**, only run the step when its condition is met.

### Confirm and Create

Summarize all collected project variables in a table and verify that they are complete and correct.

The confirmation table must include the values selected or provided by the user:

| Variable | Value | Notes |
|---|---|---|
| `FIGMA_RULE` | [Selected or provided FIGMA_RULE value] | Use this Figma file as the reference design system and component library for all screen and UI generation tasks. |
| `DESKTOP_RULE` | [Selected DESKTOP_RULE value] | Use this width for desktop screen mockups and web designs. |
| `TABLET_RULE` | [Selected TABLET_RULE value] | Use this width for tablet screen mockups. |
| `MOBILE_RULE` | [Selected MOBILE_RULE value] | Use this width for mobile screen mockups. |
| `COUNTRY_RULE` | [Selected COUNTRY_RULE value] | Use this country or countries to make sure screens and UI elements follow applicable laws and appropriate regional conventions. |
| Compliance Mode | [Selected Compliance Mode, if applicable] | Apply the selected compliance approach when multiple countries are specified. |
| `DESIGN_LIBRARIES` | [Selected or provided DESIGN_LIBRARIES value] | Use the specified design library or design system as a reference when generating screens and UI elements. |

Do not use example values, default values, or placeholder values in the confirmation table when the user has already provided a value.

Ask the user to confirm whether the collected configuration is complete and correct.

- **If confirmed:** Create `00_project-context/project-settingss.md`.
- **If corrections are requested:** Update only the affected values, then show the updated confirmation table and ask for confirmation again.
- **If variables are still missing:** Ask only for the missing variables before showing the confirmation table again.

Use `02_other files/template/project-settings.md` as the reference template when creating the file.

The generated `00_project-context/project-settingss.md` file must use this exact front matter:

---
name: project-settingss
description: Defines project-wide variables for Figma UI generation, including the reference Figma design system and component library, standard desktop, tablet, and mobile screen widths, and South Korea as the regional context for legal and UI considerations. These variables are used together with general-rules.md when generating screens and UI elements.
---

Do not modify, shorten, paraphrase, or otherwise alter this front matter.

The content after the front matter must follow the established variable format:

1. Start with `## Project Variables`.
2. Define each project variable as its own `### VARIABLE_NAME` section.
3. Use the appropriate field label for each variable, such as `Figma File`, `Size`, or `Country`.
4. Insert the exact value selected or provided by the user.
5. Follow each variable with an instruction describing how the AI should use it.
6. Separate each variable section with `---`.
7. Do not include a `## How to Use These Variables` section.
8. Do not remove, rename, or restructure existing variables unless explicitly instructed by the user.
9. If additional variables are introduced in future steps, add them as new `### VARIABLE_NAME` sections using the same format.
10. Additional variables must be added without changing the established front matter or the format of existing variables.

## Other Files

- `general-rules.md` — The AI reads this file to know how to act.