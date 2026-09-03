# UI / Screen Draft Requirements Guide

*A step-by-step guide for turning a client request into a clear, complete set of screen requirements — usable by designers, and structured enough for AI-assisted generation.*

---

## Step 1 — Understand the Client Request

Before identifying screens, make sure the actual request is clear. Read (or ask about) the client's brief, PRD, or notes, and confirm:
- What problem are they trying to solve?
- What's the core feature or journey they're asking for?
- What's explicitly in scope, and what's not?

---

## Step 2 — Identify the User Journey

Map out the path a user takes to accomplish their goal, start to finish — not the screens yet, just the *journey* (e.g. "browse products → add to cart → checkout → confirmation").

---

## Step 3 — Identify the Required Screens

Using the journey as a base, break it down into the actual screens needed.

- **List all screens** — write down every screen implied by the journey, even minor ones (e.g. confirmation modals, error states as their own screen if complex enough).
- **Group screens by journey / feature** — organize screens under the flow they belong to, especially useful if there are multiple journeys in one project.
- **Identify required vs. optional screens** — mark which screens are essential to the core flow, and which are nice-to-have or stretch scope.

---

## Step 4 — Create the Screen Inventory

For every screen identified in Step 3, capture the basics in a simple inventory:
- **Screen name**
- **Purpose** — what this screen is for
- **User** — who uses this screen
- **Entry point** — how the user arrives here
- **Primary action** — the main thing the user does on this screen
- **Priority** — required or optional

---

## Step 5 — Define Each Screen

For each screen, go deeper than the inventory and define:
- **Content** — what information/text/media appears
- **Components** — which UI components are needed (buttons, inputs, cards, etc.)
- **Actions** — what the user can do
- **Data** — what data is displayed, entered, or required
- **Business rules** — any logic or constraints (e.g. "promo code must be valid before Place Order is enabled")

---

## Step 6 — Define Screen States

Every screen can exist in more than one state. Define what each looks like for:
- Default
- Loading
- Empty
- Error
- Success
- Disabled
- (and any other relevant state for that screen)

---

## Step 7 — Define Screen Relationships

Map how each screen connects to others:
- **Previous screen** — where the user came from
- **Current screen** — this screen
- **Next screen** — where the user goes next
- **Navigation** — how they move (button, tab, back arrow, etc.)

---

## Step 8 — Identify Design System Requirements

Note which design system tokens, components, and patterns this screen should use — and flag anything that doesn't exist yet in the design system.

---

## Step 9 — Identify Responsive / Accessibility / Technical Requirements

Define how the screen behaves across breakpoints (desktop/mobile), any accessibility requirements (contrast, touch target size, screen reader considerations), and any technical constraints (e.g. platform limitations).

---

## Step 10 — Define Acceptance Criteria

For each screen, define what "done and correct" looks like — the specific, checkable conditions that confirm the screen meets requirements.

**Why it matters:** Acceptance criteria turn subjective review ("does this look right?") into an objective check ("does this meet what we defined?") — useful for both human review and AI-generated output validation.

---

*Guide version: [August 20, 2026] 