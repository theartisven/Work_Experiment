---
name: figma-spelling
description: "Read-only spelling check of Figma text layers for typos, doubled letters, and wrong words. Use for /figma-spelling or requests to proofread a Figma design."
---

# /figma-spelling - Spelling Check

Read-only. Make zero writes.

## Scope

Use `get_selection`. If empty, use `get_page_nodes`. Never full-file without confirmation.

## Collect Text

Call `get_node_children` recursively. For each node where `type = TEXT`:
- Read `characters` via `get_node_properties`.
- Record `name` and full path (build from ancestor names).
- Include overridden text in instances — read from the instance node, not the master.

Skip nodes where `characters` matches lorem ipsum patterns or is empty.

## Checks

Run against `characters` for each text node:

- Misspellings: typos, doubled letters, wrong words.
- Repeated words: `\b(\w+)\s+\1\b`.
- Split words: words broken across a `\n` where the concatenation is a valid word.
- Mixed casing: `[a-z][A-Z]` within a word not at a boundary.
- Letter/number substitution: `0` ↔ `O`, `1` ↔ `l`/`I`.

Locale: use file locale if available. Default to `en-US`. Note locale used in output.

Skip: brand names, all-caps tokens, project word list terms (load from file variables or annotations if present).

## Word List

If a project word list exists (stored as a file variable or annotation), load it before checking. When the user accepts a flagged word, add it to the list and report `accepted: word`.

## Output

When issues exist:

`## Spelling Issues`

One line per issue:

`full layer path | wrong word | suggested correction`

If none: `No spelling issues detected.`
