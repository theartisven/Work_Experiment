---
name: detect-change
description: Notice when a fact, plan, preference, or status has shifted from what was previously recorded.
---

# Detect a change

## When to select

Select this rule when a span says a fact, plan, preference, or status is no longer true or has been replaced, cancelled, moved, or updated. Signals include "actually", "switched to", "no longer", and "moved to".

## Instructions

1. Name the thing that changed.
2. State its old and new values.
3. Check `memory-bank.md`. If it contains the old value, mark that entry as superseded instead of deleting it.

## Output

`- Changed: <thing> was <old>, now <new> (span <id>)`
