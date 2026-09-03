---
name: rules-generate
description: Generate Figma designs from project rules. This skill auto-starts when you ask to generate. It applies Auto Layout, enforces 8pt spacing grids, uses semantic naming, and generates design patterns. It checks design libraries first. It asks for screen size, theme, and fidelity level. It handles complex tasks by breaking them into segments. It provides Figma links after each screen.
original-author: sven hero kaufmann
contributor:
  - theodore galve
version: 1.7
---

### Other Files to Reference When Generating

- `01_project-context/rules-thinking.md` — Thinking and reasoning rules for the AI.
- `01_project-context/project-settings.md` — Project variables (e.g. repeat value). Check current settings before generating.

---

## Before You Start

### Step 1: Gather Requirements

Ask the user for:

- **Screen size**: Desktop · Tablet · Mobile
- **Theme**: Light Mode · Dark Mode
- **Fidelity**: Wireframe · Low Fi Mockup · High Fi Mockup

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

# 
## Layout and Spacing

**Auto Layout:**
- Apply Auto Layout to every screen and element you create or edit.

**Forms:**
- Group related fields with consistent visual appearance.
- Avoid generic field labels.

**Components:**
- After using a component, verify it works correctly.
- If a component is broken, reset it before continuing.

**Spacing and padding:**
- Use multiples of 8 only.

**Number:**
- For any property like x position or width, only use whole number

**Text layers:**
- Do not set fixed width or height.
- Use `Hug` or `Fill` instead.

---

## Patterns and Generation

**Design patterns:**
- Always use the most common design pattern for the requested task.

**Images and video:**
- Always use `Fit`.


---

## Naming and Documentation

**Layer names:**
- Use semantic names.
- Use BEM naming as a reference.
- No `-` or `_` in block names.

---

## Anti-AI Design Rules

Avoid defaulting to generic AI-generated design patterns. Specifically:

### Layout & Composition
- No centered hero sections with headline + subtext + two side-by-side buttons unless the content genuinely calls for it.
- No symmetric 3-column grids used regardless of actual content count.
- No decorative lines or bars placed under headings.
- No mechanically even spacing everywhere — vary density based on content importance.


### Color & Effects
- No purple-to-blue gradient backgrounds or decorative blurred gradient blobs.
- No overly saturated violet/indigo as a default accent color.
- No rainbow or multi-color gradients on buttons or icons.
- No soft drop shadows applied to everything — use shadow sparingly and with clear purpose.
- No glassmorphism or frosted-blur effects used decoratively without functional reason.


### Typography

- No defaulting to Inter, Poppins, or Manrope — use only the brand's actual typeface.
- No oversized bold headlines with unnecessarily tight letter spacing on every screen.
- No identical font weight and size hierarchy across every screen regardless of content.


### Shape & Components

- No uniform rounded corners on every card, button, and input — mix sharp and rounded intentionally.
- No identical cards regardless of content — vary size and layout based on what they hold.
- No overuse of pill-shaped badges or tags.
- No emoji used as functional icons.
- No icons uniformly placed inside matching colored circles, evenly spaced.


### Imagery & Illustration

- No flat "corporate memphis"-style illustrated people.
- No generic abstract 3D blobs or shapes as filler decoration.

**Instead:** Use real photography, purposeful illustration, or leave the space empty. Negative space is better than decorative filler.

### Content & Copy

- No lorem ipsum or vague placeholder text — use real or realistic content.
- No generic CTAs ("Get Started," "Learn More," "Sign Up Now") — write CTAs that reflect the brand's voice and the specific action.
- No placeholder names like "John Doe," "Product Name," "Company Inc." — use real-sounding, contextually appropriate names.

**Instead:** Write copy that sounds like the brand actually talking. Match the domain's tone — a law firm, a café, and a streetwear label should not all sound the same.

---

## After Every Screen

- Use the exact name shown in the Figma Layers panel for the frame name: `{exactly-as-it-appears-in-layers}`
- Provide a Figma link after each screen is created.

---

## Animation

- Do not use Figma Motion when the user asks to create an animation.