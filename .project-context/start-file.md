---
name: start-file
description:
author: sven hero kaufmann
version: 1.2
---

## When to Start a Chat

1. Create `.project-context/project-variables.md`.
2. The AI uses this file for general project context.
3. Check if this file exists:
   - **If exists:** Read the file. Identify missing variables. Ask only about the missing ones.
   - **If does not exist:** Ask for all variables one at a time.

### Step 1: Ask FIGMA_RULE
"What rules should the Figma MCP use?"
(Open text input)

Wait for answer. Store value. Move to Step 2.

### Step 2: Ask DESKTOP_RULE
"Which desktop screen size?"
- `1920` — Windows Desktop
- `1440` — Apple Desktop
- `custom` — Enter a custom width

Wait for answer. Store value. Move to Step 3.

### Step 3: Ask TABLET_RULE
"Which tablet screen size?"
- `800` — Android tablet
- `768` — iPad tablet
- `custom` — Enter a custom width

Wait for answer. Store value. Move to Step 4.

### Step 4: Ask MOBILE_RULE
"Which mobile screen size?"
- `360` — Android phone
- `375` — Apple iPhone
- `custom` — Enter a custom width


Wait for answer. Store value. Move to Step 5.

### Step 5: Ask COUNTRY_RULE
"Which country or countries for this user?"
- `custom` — Enter country name(s)

(Accept single or multiple countries separated by commas. Example: "US, UK, Germany")

Wait for answer. If multiple countries entered, move to Step 5b. If single country, store value and move to Step 6.

### Step 5b: Ask Compliance Mode
"You selected multiple countries. Which approach for conflicting rules?"

**Overlap Mode:**
- Follow rules that apply to all countries or majority (>50%).
- Flag rules that don't overlap in a summary.
- Best for: global audiences where some regional rules can be waived.

**Strict Mode:**
- Follow all rules from every country.
- Prioritize the strictest requirement if rules conflict.
- Best for: legal/security-critical work where compliance is mandatory.

Wait for answer. Store value. Move to Step 6.

### Step 6: Confirm
Summarize all values collected. Ready to create `.project-context/project-variables.md`.

## Other Files

- `general-rules.md` — The AI reads this file to know how to act.