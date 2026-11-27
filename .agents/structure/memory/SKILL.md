---
name: memory
description: "Build or update a memory bank from a long conversation or document, or maintain one incrementally when requested. Use this skill to extract durable facts, entities, episodes, changes, and goals with a span-based workflow. For ongoing memory capture, check for updates after every 3 user messages."
---

# Build a memory bank

Select extraction rules for each span instead of applying one summary prompt to the entire input.

For ongoing memory capture, check the conversation after every 3 user messages and add any new durable information to the memory bank. Do not add an entry when there is no useful new information. This cadence applies while the skill is active; it does not trigger the skill in otherwise unrelated conversations.

## Rules

| File | Use it to |
| --- | --- |
| `memory/extract-facts.md` | Capture concrete, reusable facts |
| `memory/track-entities.md` | Track people, places, and objects |
| `memory/summarize-episode.md` | Compress a sequence of events |
| `memory/detect-change.md` | Record a change in state |
| `memory/identify-goals.md` | Identify intent and objectives |

## Workflow

### 1. Split the input

Keep each span to one or two turns and about 400 tokens, whichever limit comes first.

### 2. Select rules for each span

Choose the two or three rules that best fit the span. Ask whether it contains reusable facts, recurring entities, a goal shift, a state change, or a sequence of events. Read each selected rule file before extracting memories.

For example, use `extract-facts.md` and `track-entities.md` for a person's job history. Use `detect-change.md` and `identify-goals.md` when a plan is abandoned.

### 3. Write entries

Follow each selected rule's instructions. Write one or more entries in this format:

```text
- [RULE_NAME] [span-id or turn] <memory content>
```

### 4. Update the bank

Check `memory-bank.md` for duplicates. Append each entry under the matching section, and merge or skip near-duplicates.

### 5. Refine when needed

After a task, if recall quality was poor, follow the process in `evolution/designer.md`.
