---
name: "figma-audit"
description: "Audit Figma designs: check spelling, accessibility (WCAG), design patterns, and CRO opportunities. Read-only."

dateCreated: 2026-11-05T09:42:16+08:00
dateUpdated: 2026-11-05T10:06:31+08:00
hasBasicImage: false
basicImage: 
---

# /figma-audit - Figma Design Audits

## Commands

- `/figma-audit help` → print command list
- `/figma-audit` (no arg) → run all: spelling → a11y → pattern → cro
- `/figma-audit spelling` → spelling check only
- `/figma-audit a11y` → accessibility assessment only
- `/figma-audit pattern` → design pattern gap check only
- `/figma-audit cro` → CRO improvement list only

## Spelling Check

Find every text layer in scope. Check for likely misspellings (typos, doubled letters, wrong words). Ignore brand names, intentional stylization, lorem ipsum.

Format: one line per issue - `layer name | wrong word`

If nothing found: "No spelling issues detected."

## Accessibility Assessment

Check and list issues for:

- **Color contrast**: text vs background. Flag if below WCAG AA (4.5:1 normal, 3:1 large text 18pt+bold or 24pt+). Format: `layer name | ratio found | required`
- **Text size**: body text under 12px flagged as too small. Format: `layer name | size | issue`
- **Touch targets**: interactive elements (buttons, tappable icons) smaller than 44×44px. Format: `layer name | size | issue`
- **Color-only signaling**: information conveyed by color alone (red text for errors with no icon/label). Format: `layer name | issue | recommendation`
- **Missing alt equivalents**: images/icons conveying meaning with no adjacent label or accessible name. Format: `layer name | issue | recommendation`

If nothing found: "No accessibility issues detected."

## Design Pattern Gap Check

1. Identify screen/flow type from content and layout (login form, checkout, pricing table, product listing, onboarding, settings)
2. Compare against standard elements for that pattern (e.g., login: email/username field, password field, show-password toggle, forgot-password link, primary button, error-state slot, alternate auth)
3. Format: one line per missing element - `expected element | why typically included`

If nothing found: "No pattern gaps detected."

## Cro Improvement List

Evaluate for conversion opportunities: CTA visibility/placement, form friction, trust signals, urgency/scarcity cues, value-prop clarity, competing CTAs, social proof, checkout/step count, error-recovery clarity.

For each improvement, name the change and metric it moves (CTR, form completion, cart abandonment, signup conversion, bounce rate, time-to-first-action).

Format: one line per improvement - `improvement | metric`

If nothing found: "No CRO improvements identified."

## Output Contract

Make zero edits. Output only specified list format. Never pad with commentary outside list.