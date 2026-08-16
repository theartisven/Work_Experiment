# Design System Documentation Template

> A reusable template for documenting design systems from Figma. Update sections with your own values.

---

## Overview

**Design System Name:** [Your Design System Name]  
**Version:** 1.0.0  
**Last Updated:** [Date]  
**Owner/Team:** [Team Name]  

Brief description of the design system's purpose and scope.

---

## Table of Contents

1. [Color Variables](#color-variables)
2. [Spacing Variables](#spacing-variables)
3. [Typography Styles](#typography-styles)
4. [Component Styles](#component-styles)
5. [Naming Conventions](#naming-conventions)
6. [Usage Guidelines](#usage-guidelines)

---

## Color Variables

### Collection: Colors Token

**Description:** Primary color tokens used across the design system.  
**Type:** COLOR  
**Scopes:** ALL_SCOPES

| Variable Name | Description | Use Case |
|---|---|---|
| PrimaryColor | Primary color used for key elements | Buttons, highlights, CTAs |
| SecondaryColor | Secondary color for CTAs, icons, or emphasis | Secondary actions, icons |
| ErrorColor | Color for error messages | Warnings, alerts, validation errors |
| SuccessColor | Color for success messages | Confirmations, success states |
| TextLinkColor | Color for clickable text | Links, hyperlinks |
| PrimaryTextColor | Color for main text | Headings, body text |
| SecondaryTextColor | Color for secondary text | Subheadings, helper text |
| DisabledTextColor | Color for text in disabled state | Disabled buttons, inputs |
| PrimaryBackgroundColor | Background color for main areas | Sections, containers |
| BorderColor | Default border color | Input borders, dividers |
| SectionColor | Section background color | Card backgrounds, panels |

### Collection: [Additional Color Collection]

**Description:** [Description of this collection]  
**Type:** COLOR  
**Scopes:** [Applicable scopes]

| Variable Name | Description | Use Case |
|---|---|---|
| [Variable] | [Description] | [Use Case] |

---

## Spacing Variables

### Collection: Spacing

**Description:** Numeric spacing scale for padding, margins, and gaps.  
**Type:** FLOAT  
**Scopes:** WIDTH_HEIGHT, GAP

| Variable Name | Value | Use Case |
|---|---|---|
| Spacing/0 | [Value] | No spacing |
| Spacing/1 | [Value] | Minimal spacing |
| Spacing/3 | [Value] | Small spacing |
| Spacing/4 | [Value] | Standard spacing |
| Spacing/6 | [Value] | Medium spacing |
| Spacing/8 | [Value] | Large spacing |
| Spacing/9 | [Value] | Extra large spacing |

**Usage Pattern:**  
Variables are named using a slash notation: `Category/Scale` (e.g., `Spacing/4`).

---

## Typography Styles

### Collection: Typography

**Description:** Type styles for headings, body text, and labels.  
**Type:** TYPOGRAPHY

| Style Name | Font Family | Size | Weight | Line Height | Use Case |
|---|---|---|---|---|---|
| Heading/Large | [Font] | [Size] | [Weight] | [Height] | Page titles, H1 |
| Heading/Medium | [Font] | [Size] | [Weight] | [Height] | Section titles, H2 |
| Heading/Small | [Font] | [Size] | [Weight] | [Height] | Subsections, H3 |
| Body/Regular | [Font] | [Size] | [Weight] | [Height] | Body text, paragraphs |
| Body/Small | [Font] | [Size] | [Weight] | [Height] | Captions, helper text |
| Label/Medium | [Font] | [Size] | [Weight] | [Height] | Button labels, tags |

---

## Component Styles

### Collection: Components

**Description:** Reusable styles for common component patterns.  
**Type:** PAINT (or EFFECT/GRID as applicable)

| Style Name | Description | Applied To |
|---|---|---|
| Button/Primary | Style for primary action buttons | Button components |
| Button/Secondary | Style for secondary action buttons | Button components |
| Input/Default | Default input field style | Text inputs |
| Card/Elevated | Elevated card shadow effect | Card containers |
| Divider/Light | Light divider line | Separators |

---

## Naming Conventions

### Variables

**Pattern:** `[Category]/[Descriptor]` or `[Purpose][Type]`

- **Colors:** PascalCase + descriptive (e.g., `PrimaryColor`, `ErrorColor`, `TextLinkColor`)
- **Spacing:** `Spacing/[Scale]` (e.g., `Spacing/4`, `Spacing/8`)
- **Sizing:** `Size/[Scale]` (e.g., `Size/Small`, `Size/Medium`)
- **Opacity:** `Opacity/[Level]` (e.g., `Opacity/50`, `Opacity/100`)

### Styles

**Pattern:** `[Component]/[State]` or `[Purpose]/[Variant]`

- **Typography:** `[Level]/[Size]` (e.g., `Heading/Large`, `Body/Regular`)
- **Components:** `[Component]/[Variant]` (e.g., `Button/Primary`, `Input/Error`)
- **Effects:** `[Effect]/[Intensity]` (e.g., `Shadow/Light`, `Blur/Medium`)

### Organization

- **Hierarchy:** Group related items with forward slashes (e.g., `Color/Text/Primary`)
- **Ordering:** Use numeric prefixes for collections (e.g., `02_Colors Token`)
- **Consistency:** Apply the same naming structure across all tokens

---

## Usage Guidelines

### Variables

1. **Always use variables** instead of hardcoding color values
2. **Organize variables** into logical collections (Colors, Spacing, Typography)
3. **Document purposes** in descriptions for clarity
4. **Define scopes** appropriately (ALL_SCOPES, WIDTH_HEIGHT, GAP, etc.)
5. **Use consistent naming** following the established patterns

### Styles

1. **Create styles** for frequently repeated combinations
2. **Use meaningful names** that describe the style's purpose
3. **Document variations** (e.g., primary vs. secondary, light vs. dark)
4. **Avoid overly specific names** that limit reusability
5. **Maintain hierarchy** in style organization

### Best Practices

- ✅ Use semantic names (e.g., `PrimaryColor` vs. `BlueColor`)
- ✅ Group related tokens together
- ✅ Include descriptions for all tokens
- ✅ Test variables across multiple modes (light/dark, etc.)
- ✅ Document the purpose and usage of each token
- ❌ Avoid abbreviations that reduce clarity
- ❌ Don't mix naming conventions within collections
- ❌ Avoid overly nested hierarchies (keep depth reasonable)

---

## Implementation References

### Figma File Structure

```
design_systems/
├── [Design System Name]/
│   └── variables/
│       ├── [01_Collection Name]/
│       │   ├── color/
│       │   ├── float/
│       │   ├── string/
│       │   └── boolean/
│       ├── [02_Collection Name]/
│       └── [03_Collection Name]/
```

### File Paths

Variables are organized as:  
`design_systems/[System Name]/variables/[Collection]/[Type]/[Variable Name]`

Example:  
`design_systems/Kawasaki India UI Sample/variables/02_Colors Token/color/PrimaryColor`

---

## Maintenance

### Quarterly Reviews

- [ ] Audit variable usage across components
- [ ] Check for unused or redundant tokens
- [ ] Validate naming consistency
- [ ] Update documentation

### When Adding New Variables

1. Determine the appropriate collection
2. Follow established naming conventions
3. Add descriptive documentation
4. Define applicable scopes
5. Test across all modes
6. Update this documentation

---

## Related Documents

- [Component Library](link-to-components)
- [Brand Guidelines](link-to-brand)
- [Development Guide](link-to-dev-guide)
- [Accessibility Standards](link-to-a11y)

---

## Changelog

| Version | Date | Changes |
|---|---|---|
| 1.0.0 | [Date] | Initial template creation |
| | | |

---

**Questions?** Reach out to [Contact/Team Name] for support.
