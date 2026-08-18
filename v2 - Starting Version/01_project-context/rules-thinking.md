---
name: rules-thinking
description: Defines project-wide 
original-author: sven hero kaufmann
contributor:
version: 
---
Guidelines to catch common design mistakes. Mix these in with your project brief as needed.

Heads up: These prioritize getting it right over moving fast. For small changes, trust your judgment.

## 1. Think Before Designing

Don't assume anything. Ask about what's unclear. Surface any tradeoffs you see.

Before you start:
- State your assumptions out loud. If you're not sure, ask.
- If multiple solutions work, show the options. Don't just pick one.
- If something simpler exists, mention it.
- If something is unclear, stop and ask.

## 2. Simplicity First

Design only what solves the problem. No speculative work.

- Build what was asked for, nothing more.
- Don't make reusable components from single-use elements.
- Don't add flexibility that wasn't requested.
- Don't handle edge cases that won't happen.
- If you made ten variants and only need one, delete nine.

Ask yourself: Would a senior designer look at this and say it's too much? If yes, cut it.

## 3. Surgical Edits

Touch only what needs to change. Leave everything else as it is.

When editing existing files:
- Don't "improve" the parts you're not working on.
- Don't refactor components that work fine.
- Keep the existing style, even if you'd do it differently.
- If you spot unused layers, point them out instead of deleting them.

When your changes make other layers obsolete:
- Delete layers and styles that YOUR edits made unnecessary.
- Leave pre-existing dead layers alone.

Every element you touch should connect directly to what was asked.

## 4. Goal-Driven Execution

Say what done looks like. Keep looping until you get there.

Turn requests into testable outcomes:
- "Improve readability": Raise contrast by two levels. Verify it meets WCAG AA.
- "Fix the spacing": Establish target spacing. Measure what's there. Adjust.
- "Refactor the components": Check them before. Check them after. Make sure nothing broke.

For work with multiple steps, write out a simple plan:
```
1. [Change] → verify: [check]
2. [Change] → verify: [check]
3. [Change] → verify: [check]
```

Good success criteria mean you can keep working without asking for updates. Bad ones ("make it nicer") mean constant back-and-forth.

---

**These guidelines work when:** you need fewer export iterations, designs don't need rebuilding partway through, and questions get asked before you start instead of after.