---
name: fix
metadata:
  version: 1.8.0
description: >
  Clean up a Figma design/file: fix auto layout, snap padding/radius/font-size/x/y/width/height
  to an 8pt grid, fix whitespace, remove unused/empty/dead layers, rename layers using BEM,
  find text layers with possible spelling errors, fix visual hierarchy, assess accessibility,
  find missing elements vs common design patterns, list CRO improvements, flatten deeply
  nested layer groups, and optically align elements. Trigger on "/fix", "/fix help", "/fix
  autolayout", "/fix grid", "/fix whitespace", "/fix remove", "/fix rename", "/fix spelling",
  "/fix focus", "/fix impairment", "/fix pattern", "/fix cro", "/fix flatten", "/fix optical",
  or any request to clean up, tidy, normalize, or
  audit a Figma file/selection (auto layout, 8pt grid, BEM naming, spelling, hierarchy,
  accessibility, missing patterns, CRO, flattening nested groups, optical alignment). Requires
  a connected Figma MCP/plugin tool that reads/writes node properties — if none connected, say
  so and stop (except `/fix help`, which needs no connection).
---
/
 
# /fix — Figma Clean-Up
 
## Command routing
- `/fix help` → print the command list below. No Figma connection needed.
- `/fix` (no arg) → run ALL edit-making sections, in order: autolayout → grid → whitespace →
  remove → rename → focus → optical. (`spelling`, `impairment`, `pattern`, and `cro` are
  read-only audits, excluded from the "run everything" default — run them only when named
  explicitly, since they report rather than edit.)
- `/fix autolayout` → "Fix Auto Layout" only.
- `/fix grid` → "Snap to 8pt Grid" only.
- `/fix whitespace` → "Fix Whitespace" only.
- `/fix remove` → "Remove Useless Layers" only.
- `/fix rename` → "Rename with BEM" (read-only).
- `/fix spelling` → "Spelling Check" only (read-only).
- `/fix focus` → "Fix Visual Hierarchy" only.
- `/fix impairment` → "Accessibility Assessment" only (read-only).
- `/fix pattern` → "Design Pattern Gap Check" only (read-only).
- `/fix cro` → "CRO Improvement List" only (read-only).
- `/fix flatten` → "Flatten Deep Nesting" only.
- `/fix optical` → "Optical Alignment" only.
Natural-language requests map to whichever section(s) match; if ambiguous, run all edit-making
sections (same as `/fix`).

### `/fix help` output
List, one line each: `/fix <command> — <one-line description>`, covering: help, (no arg/all),
autolayout, grid, whitespace, remove, rename, spelling, focus, impairment, pattern, cro,
flatten, optical. Keep each description to a single short sentence pulled from the section
headers below.
 
## Preconditions
Check for a connected Figma tool (MCP server or plugin bridge) that can list nodes and set
node properties. If none available, tell user to connect one and stop — do not guess at file
contents. `spelling`, `impairment`, `pattern`, `cro`, and `help` are read-only/no-op and only
need list/read access (help needs no access at all).
 
Scope: current selection if one exists, else the whole page.
 
---
 
## Fix Auto Layout
use attach file as a reference t
- Apply auto layout (direction = row or column, matching visual arrangement).
- Set gap = observed spacing, snapped per Grid rules below.
- Set resizing: hug contents unless the frame is clearly meant to fill parent (e.g. full-width
  section) — then set fill container.
For frames that already have auto layout but inconsistent padding/gap: normalize so all sides
use consistent values (don't flatten an intentionally asymmetric layout, e.g. a header).
## Snap to 8pt Grid
Applies to: padding (all 4 sides), corner radius, font size, gap/spacing, x, y, width, height.
Rule: round to nearest multiple of 8, EXCEPT allow multiples of 4 for values under 16 (common
for small radii/gaps like 4, 12). Never leave a decimal.
`round8(v) = v<16 ? round(v/4)*4 : round(v/8)*8`
Font size: prefer nearest value from a type scale (12,14,16,18,20,24,28,32,40,48) over raw
round8 if it isn't in that set — use judgement, don't break a clearly intentional scale.
Width/height: skip aspect-ratio-locked assets (icons/images) — flag instead of forcing resize.
x/y: if node is inside an auto-layout frame, position is derived from layout — skip manual x/y
and instead ensure the frame's own x/y and item spacing are snapped.
 
## Fix Whitespace
- Normalize gap/spacing values between sibling elements to consistent, snapped (8pt/4pt)
  amounts — no two visually-equal gaps should differ by a stray 1-3px.
- Remove stray empty text nodes or spacer layers that exist only to fake spacing where auto
  layout gap/padding should be used instead.
- Trim leading/trailing whitespace inside text layer content (e.g. "Title " → "Title").
- Flag (don't silently change) any spacing that looks intentionally irregular (e.g. asymmetric
  hero section) rather than forcing uniformity.
## Remove Useless Layers
Delete/flag for deletion:
- Empty groups/frames with zero children.
- Frames/groups with exactly one child and no distinguishing style (no fill, stroke, radius,
  effect, or padding) — unwrap the child instead of deleting content.
- Duplicate layers stacked exactly on top of each other with identical properties.
- Dead layers: layers with visibility toggled off. Flag each with name + parent — don't delete
  automatically, since hidden may be intentional (alt states, unused variants kept for later).
  Ask user to confirm deletion vs keep-hidden.
Do NOT delete anything with fills, text content, effects, or component instances even if it
looks redundant — flag it for the user instead of guessing.
## Rename with BEM
Convert layer names to `block__element--modifier` format:
- block = containing component/section (e.g. `card`, `nav`, `product-list`)
- element = child part, separated by `__` (e.g. `card__title`, `card__image`)
- modifier = state/variant, separated by `--` (e.g. `button--primary`, `card__title--large`)
- lowercase, hyphen-separated words within each segment (no spaces/camelCase)
- Only add a segment when meaningful — a lone top-level frame is just `block`.
Infer block/element from visual hierarchy and content, not Figma's auto-generated names
("Frame 12", "Rectangle 4" are exactly what must be replaced).
**Repeated-block suffixes** — when the same block (e.g. `card`) appears multiple times as
siblings (candidates to become a reusable component):
- 4+ repeats → increment suffix, zero-padded 3-digit: `card-001`, `card-002`, `card-003`...
  applied after the full BEM name, e.g. `card-001__title`, `card-002__title`.
- 2-3 repeats → position suffix instead: `card-top`/`card-middle`/`card-bottom` (vertical
  stacks) or `card-left`/`card-center`/`card-right` (horizontal), whichever matches actual
  layout. Applied same way, e.g. `card-top__title`.
- Note either case in the summary as "candidate for componentization" — this skill renames but
  does not create the actual component.
## Spelling Check
Read-only — do not edit any node.
1. Find every text layer in scope.
2. Check its text content for likely misspellings (typos, doubled letters, obvious wrong
   words). Ignore brand names, intentional stylization, and placeholder lorem ipsum.
3. Output ONLY a list, one line per issue, in this exact format:
   `layer name | wrong word`
   If a layer has multiple issues, one line per word.
4. If no issues found, state that clearly instead of an empty list.
## Fix Visual Hierarchy
Goal: the eye should land on the most important element first, then flow in priority order.
- Compare font sizes/weights across headings, subheadings, and body text in scope — ensure a
  clear step between levels (e.g. don't leave an h2 the same size as body text). Bump sizes to
  the type scale used in "Snap to 8pt Grid" as needed.
- Check color/contrast weight: primary CTAs and key content should visually outrank secondary
  /tertiary elements (opacity, color saturation, or weight) — flag or adjust elements that
  compete with or outweigh the primary action.
- Check spacing-as-grouping: related elements should sit closer together than unrelated ones
  (tighten/loosen gaps so proximity reflects grouping, using Grid/Whitespace rules above).
- Check reading order top-to-bottom / left-to-right matches actual priority order; flag any
  section where a less important element is positioned/sized more prominently than a more
  important one, rather than silently reordering layers.
## Accessibility Assessment
Read-only — do not edit any node. Report findings only.
Check and list issues for:
- Color contrast: text vs background contrast ratio below WCAG AA (4.5:1 normal text, 3:1
  large text/18pt+bold or 24pt+). Report `layer name | ratio found | required`.
- Text size: body text under 12px flagged as too small.
- Touch targets: interactive elements (buttons, icons meant to be tappable) smaller than
  44x44px flagged.
- Color-only signaling: information conveyed by color alone (e.g. red text with no icon/label
  for an error) flagged.
- Missing alt-text-equivalent: images/icons that convey meaning with no adjacent label or
  accessible name available in the file.
Output format: one line per issue, `layer name | issue | recommendation`. If none found, state
that clearly.
## Design Pattern Gap Check
Read-only — do not edit any node. Report findings only.
1. Identify what kind of screen/flow is in scope (e.g. login form, checkout, pricing table,
   product listing, onboarding, settings page) from its content and layout.
2. Compare against the standard/expected elements for that pattern (established UX
   conventions — e.g. login form typically has: email/username field, password field,
   show-password toggle, forgot-password link, primary submit button, error-state slot,
   alternate-auth options; pricing table typically has: plan name, price, billing-period
   toggle, feature list, CTA per plan, "most popular" highlight, FAQ/guarantee).
3. List elements the standard pattern expects that are missing from this design.
4. Output ONLY a list, one line per missing element, in this format:
   `expected element | why it's typically included`
   If nothing is missing, state that clearly instead of an empty list.
## CRO Improvement List
Read-only — do not edit any node. Report findings only.
1. Evaluate scope for conversion-rate-optimization opportunities: CTA visibility/placement,
   friction in forms, trust signals (reviews, badges, guarantees), urgency/scarcity cues,
   value-prop clarity above the fold, number of competing CTAs, social proof placement,
   checkout/step count, error-recovery clarity.
2. For each improvement found, name the change and the metric it would most plausibly move
   (e.g. click-through rate, form completion rate, cart abandonment rate, signup conversion,
   bounce rate, time-to-first-action).
3. Output ONLY a list, one line per improvement, in this format:
   `improvement | metric it improves`
4. If nothing significant found, state that clearly instead of an empty list.
## Flatten Deep Nesting
For groups/frames nested 5+ levels deep with no styling purpose at intermediate levels (no
auto layout, no fill/stroke/effect/padding/clip at that level — pure passthrough wrappers):
- Collapse/unwrap those intermediate levels so children attach directly to the nearest
  meaningful ancestor.
- Preserve any level that adds real behavior (auto layout, clipping, effects, constraints,
  component boundary) — never flatten through a component instance boundary.
- Flag structures too ambiguous to auto-flatten (e.g. levels used purely for prototype
  interaction targets) instead of guessing.
## Optical Alignment
Snapped/geometric alignment (equal numeric x/y or centering) doesn't always look aligned to
the eye — adjust these by a few px where geometry lies:
- Icons/glyphs with uneven visual weight (e.g. triangular play icon, asymmetric arrow) next to
  text: nudge so their visual center matches the text's center, not their bounding-box center.
- Circular or rounded shapes next to square/rectangular ones: circles read as slightly smaller
  than same-size squares — nudge circle size up or position in by 1-2px to match perceived size.
- Text baseline vs icon: align icon optical center to text cap-height/baseline midpoint, not
  raw bounding box.
- Rows of mixed-shape buttons/icons: check the row reads as a straight line to the eye, not
  just equal y-coordinates.
Keep every optical nudge small (1-3px) and never move an element off the underlying 8pt/4pt
grid it belongs to — nudge within the cell, don't break grid alignment elsewhere. Flag instead
of guessing when the "correct" optical center is ambiguous.
---
 
## Output (for edit-making commands: all/autolayout/grid/whitespace/remove/rename/focus/flatten/optical)
Report a short summary: counts of frames auto-layouted, values snapped, whitespace fixed,
layers removed (with names), dead layers flagged, layers renamed (old → new), hierarchy
adjustments made, levels flattened. Flag anything skipped/uncertain (aspect-locked assets,
ambiguous BEM naming, intentionally irregular spacing, content-bearing nodes not deleted,
hierarchy calls that need a human eye, ambiguous flatten targets) for user confirmation rather
than silently guessing.
