---
name: summarize-episode
description: Compress a narrative sequence (an event, a conversation arc, a problem and its fix) into one sentence.
---

# Summarize an episode

## When to select

Select this rule when a span describes a sequence with a beginning and an outcome, such as a resolved problem, trip, debugging session, or negotiation.

## Instructions

1. Identify what started the sequence, what action followed, and what outcome resulted.
2. Include all three in one sentence.
3. Omit intermediate steps unless they explain the outcome.

## Output

Write one sentence in this format: `<trigger> led to <action>, resulting in <outcome>.`
