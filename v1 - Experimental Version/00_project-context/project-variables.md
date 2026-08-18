---
name: project-variables
description: Defines project-wide variables for Figma UI generation, including the reference Figma design system and component library, standard desktop, tablet, and mobile screen widths, and country as the regional context for legal and UI considerations. These variables are used together with general-rules.md when generating screens and UI elements.
---

## Project Variables

### FIGMA_RULE
**Figma File:** https://www.figma.com/design/fFXr0xMrf2KD43F7CoF8lD/Untitled?node-id=0-1&p=f&t=UNeo0Hg4P8IaPa1q-0

Use this Figma file as the reference design system and component library for all screen and UI generation tasks.

---

### DESKTOP_RULE
**Size:** `1920` — Windows Desktop

Use this width for desktop screen mockups and web designs.

---

### TABLET_RULE
**Size:** `768` — iPad tablet

Use this width for tablet screen mockups.

---

### MOBILE_RULE
**Size:** `360` — Android phone

Use this width for mobile screen mockups.

---

### COUNTRY_RULE
**Country:** South Korea

Use this country for make sure that any screen or elements does not violate any laws and use that to estimate the the typical elements.

---


## How to Use These Variables

1. When generating a screen, reference the appropriate size based on the target device.
2. Always consult `general-rules.md` for design system guidelines.
3. Use the Figma file above for component and style references.
