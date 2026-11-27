---
name: figma-run-all
description: "Print the Figma command list (help) or run the full sequence for a group: layout (autolayout, grid, whitespace), cleanup (remove, flatten, rename-semantic), or audit (spelling, a11y). Also supports all to chain all three groups. Use for /figma-run-all, /figma-run-all help, or requests to run all Figma layout, cleanup, or audit steps at once."
---

# /figma-run-all - Help and Run-All Sequences

## Commands

- `/figma-run-all help` → print command list. No reads or writes.
- `/figma-run-all layout` → `figma-autolayout` → `figma-grid` → `figma-whitespace`
- `/figma-run-all cleanup` → `figma-remove-layers` → `figma-flatten-layers` → `figma-rename-semantic`
- `/figma-run-all audit` → `figma-spelling` → `figma-a11y`
- `/figma-run-all consistency` → `figma-consistency` in freestyle mode (requires 2+ frames selected)
- `/figma-run-all consistency token` → `figma-consistency` in token mode (requires variables or styles in file)
- `/figma-run-all all` → layout → cleanup → audit
- Add `preview` → layout and cleanup steps show `[preview]` lines, make no writes. Audit is always read-only.

If no group named: reply with the help output and ask which group to run.

## Help Output

```
/figma-run-all help           show this list
/figma-run-all layout         autolayout → grid → whitespace
/figma-run-all cleanup        remove → flatten → rename-semantic
/figma-run-all audit          spelling → a11y
/figma-run-all consistency          cross-screen check, freestyle (2+ frames)
/figma-run-all consistency token    cross-screen check, token mode
/figma-run-all all            layout → cleanup → audit
+ preview                     show changes without writing
```

## Procedure

1. Call `get_selection` once at the start. Pass the same selection to every step — do not re-query between steps.
2. Before the first write: call `get_file_version` and record the version ID so the user can revert.
3. Run steps in order. After each step, check the step's summary line for errors or flags before continuing.
4. If a step reports an error, stop and report: `[step name] failed — stopping. Version to revert: <id>`.
5. In preview mode: collect all `[preview]` lines from every step. Output them grouped under `### [preview] step-name` headers before writing anything.
6. For `/figma-run-all all`: run audit last so it reflects the post-cleanup state.

## Progress

Print at the start of each step: `[N/total] step-name`

## Combined Output

One section per step using that step's output format. End with:

```
## Summary
Total changes: N
Flagged for review: N
File version before changes: <id>
```
