---
name: generate
description: Generate Figma designs from project rules. This skill auto-starts when you ask to generate. It applies Auto Layout, enforces 8pt spacing grids, uses semantic naming, and generates design patterns. It checks design libraries first. It asks for screen size, theme, and fidelity level. It handles complex tasks by breaking them into segments. It provides Figma links after each screen.
original-author: sven hero kaufmann
contributor:
  - theodore galve
version: 1.7
---

### Open this
- `file_made/PROJECT-SETTTING.md` — Project variables (e.g. repeat value). Check current settings before generating.

---

## Before You Start

### Step 1: Gather Requirements

Ask the user for:

- **Screen size**: Desktop · Tablet · Mobile
- **Theme**: Light Mode · Dark Mode
- **Fidelity**: Wireframe · Low Fi Mockup

### Step 2: Interview & Clarify

- Conduct targeted questions until you reach shared understanding.
- Work in **rounds**: identify all decisions whose prerequisites are met (the "frontier"). 3–5 rounds total.
- Ask all frontier questions in one round using this format:

```
❓ **Q1** — **<question title>**: <question body, including multiple choices if needed>

➡️ <your recommended answer>
```
- Research facts yourself — don't ask the user to find them.
- Before designing, summarize the content in bullet points.
- Get user approval before generating UI.

### Step 3: Check Design Libraries

- Ask if using a design library or from scratch

---
# Design Rules & Guidelines

## Layout and Spacing

| Rule | Status | Details |
|------|--------|---------|
| Generic field labels | Forbid | Do not use generic field labels. |
| Text layer width/height | Forbid | Do not set a fixed width or height. Use Hug or Fill instead. |
| Auto Layout | Allow | Apply to every screen and element. |
| Forms | Allow | Group related fields. Use the same visual style for each group. |
| Components | Allow | After use, check that it works. If broken, reset it. Then continue. |
| Spacing and padding | Allow | Use multiples of 8 only. |
| Numbers | Allow | Use whole numbers for all properties (position, width, etc.). |

---

## Patterns and Generation

| Rule | Status | Details |
|------|--------|---------|
| Design patterns | Allow | Use the most common design pattern for the task. |
| Images and video | Allow | Use Fit. |

---

## Naming and Documentation

| Rule | Status | Details |
|------|--------|---------|
| Separators in block names | Forbid | Do not use - or _ in block names. |
| Layer names | Allow | Use semantic names. |
| BEM naming | Allow | Use BEM (Block Element Modifier) as a reference. |

---

## Design Rules

### Layout and Composition

| Rule | Status | Details |
|------|--------|---------|
| Centered hero sections | Forbid | Do not center every hero section with headline, subtext, and two buttons side by side. |
| Symmetric 3-column grid | Forbid | Do not use a symmetric 3-column grid for all content. |
| Decorative lines under headings | Forbid | Do not put decorative lines or bars under headings. |
| Uniform spacing | Forbid | Do not use the same spacing everywhere. |
| Asymmetric layouts | Allow | Use asymmetric layouts based on content hierarchy. |
| Space allocation | Allow | Give more space to the most important content. |
| Layout variety | Allow | Use 2-column splits, staggered layouts, or single-column sections when they fit. |
| Density variation | Allow | Change density based on content importance. |

---

### Color and Effects

| Rule | Status | Details |
|------|--------|---------|
| Purple-to-blue gradients | Forbid | Do not use purple-to-blue gradients or blurred gradient blobs in the background. |
| Saturated violet/indigo accent | Forbid | Do not use saturated violet or indigo as the default accent. |
| Rainbow/multi-color gradients | Forbid | Do not put rainbow or multi-color gradients on buttons or icons. |
| Soft drop shadows everywhere | Forbid | Do not add soft drop shadows to everything. |
| Decorative glassmorphism | Forbid | Do not use glassmorphism or frosted-blur for decoration only. |
| Base palette | Allow | Start with a simple base palette. Add one accent color with a clear purpose. |
| Contrast and spacing for depth | Allow | Use contrast and spacing to create depth. |
| Purposeful shadows | Allow | Use shadows with a clear purpose. |
| Purposeful blur or glass | Allow | Use blur or glass only when it helps the user. |

---

### Typography

| Rule | Status | Details |
|------|--------|---------|
| Default system fonts | Forbid | Do not default to Inter, Poppins, or Manrope. |
| Oversized bold headlines | Forbid | Do not use oversized bold headlines with tight letter spacing on every screen. |
| Uniform hierarchy | Forbid | Do not use the same font weight and size hierarchy on every screen. |
| Brand typeface | Allow | Use the brand typeface only. |
| Typographic hierarchy | Allow | Use weight, size, and case to show hierarchy. |
| Screen-specific hierarchy | Allow | Change the type hierarchy for each screen based on its content. |

---

### Shape and Components

| Rule | Status | Details |
|------|--------|---------|
| Uniform rounded corners | Forbid | Do not use uniform rounded corners on every card, button, and input. |
| Identical cards | Forbid | Do not make all cards look the same. |
| Pill-shaped badges/tags | Forbid | Do not overuse pill-shaped badges or tags. |
| Emoji as icons | Forbid | Do not use emoji as functional icons. |
| Icons in colored circles | Forbid | Do not place all icons inside matching colored circles at equal spacing. |
| Component shape and size | Allow | Match component shape and size to the content inside. |
| Card size variation | Allow | Change card size and layout based on content type. |
| Brand-aligned icons | Allow | Use icons that match the brand visual style. |

---

### Imagery and Illustration

| Rule | Status | Details |
|------|--------|---------|
| Corporate memphis style | Forbid | Do not use flat, "corporate memphis"-style illustrated people. |
| Generic 3D blobs | Forbid | Do not use generic abstract 3D blobs or shapes for decoration. |
| Purposeful imagery | Allow | Use real photos or illustration with a clear purpose. |
| Empty space | Allow | Leave space empty. Empty space is better than filler. |

---

### Content and Copy

| Rule | Status | Details |
|------|--------|---------|
| Lorem ipsum | Forbid | Do not use lorem ipsum or vague placeholder text. |
| Generic CTAs | Forbid | Do not use generic CTAs: "Get Started," "Learn More," "Sign Up Now." |
| Generic placeholders | Forbid | Do not use "John Doe," "Product Name," or "Company Inc." |
| Uniform brand voice | Forbid | Do not write copy that sounds the same for every brand or industry. |
| Realistic content | Allow | Use real or realistic content. |
| Brand-aligned CTAs | Allow | Write CTAs that match the brand voice and the specific action. |
| Contextual names | Allow | Use names that fit the context and sound real. |
| Industry-appropriate tone | Allow | Match the tone to the industry. A law firm and a cafe sound different. |

---

## After Every Screen

| Rule | Status | Details |
|------|--------|---------|
| Frame naming | Allow | Use the exact name shown in the Figma Layers panel for the frame name: {exactly-as-it-appears-in-layers}. |
| Figma link | Allow | Provide a Figma link after each screen is created. |

---

## Animation

| Rule | Status | Details |
|------|--------|---------|
| Figma Motion | Forbid | Do not use Figma Motion when the user asks to create an animation. |

---

## Glossary

| Term | Definition |
|------|------------|
| BEM | Block Element Modifier |
| CTA | Call to Action |