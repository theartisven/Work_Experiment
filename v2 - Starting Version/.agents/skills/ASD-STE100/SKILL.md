---
name: asd-ste100
description: >
  Rewrites text to comply with ASD-STE100 (Simplified Technical English) rules.
  Two modes: normal (full rule set) and relax (same rules but banned word list is lifted).
  Trigger on /asd-ste100, /asd-ste100 relax, or any request to rewrite using STE, Simplified Technical English, or ASD rules.
  Also trigger when the user says "rewrite this in STE", "make this STE compliant", or "simplify to STE100".
  Always use this skill for those phrases — do not attempt STE rewrites without it.
---

# ASD-STE100 Rewrite Skill

Rewrites input text to comply with ASD-STE100 Simplified Technical English.

---

## Trigger

- `/asd-ste100` — full rule set (default, **normal** mode)
- `/asd-ste100 relax` — same rules, **banned word list is disabled** (relax mode)

If no mode is given, use **normal** mode.

---

## Modes

### Normal Mode

Apply all rules below, including the banned word list.

### Relax Mode

Apply all rules below. **Skip the banned word check.** All other rules still apply.

Add a header note at the top of the output:

> ⚠️ Relax mode: banned word list is not applied.

---

## Core ASD-STE100 Rules

Apply these rules to every rewrite, in both modes.

### 1. Sentence Structure

- Maximum **20 words** per sentence for procedural (instruction) sentences.
- Maximum **25 words** per sentence for descriptive sentences.
- One instruction per sentence. Do not combine two actions with "and."
- Use active voice. Avoid passive voice.
- Write in the present tense for procedures. Use simple past only when describing a completed event.

Not correct:

> "The valve should be turned clockwise until the pressure has been equalized."

Correct:

> "Turn the valve clockwise. Equalize the pressure."

### 2. Approved Verbs

- Use one word for one meaning. Do not use the same word for two different actions.
- Use the most basic, common English verb. Prefer: check, install, remove, connect, use, start, stop, set, open, close, apply, put.
- Do not use noun clusters as verbs (e.g., "effect a repair" → "repair").

### 3. Approved Words (Normal Mode Only)

STE maintains an approved word list. Common banned or discouraged words and their replacements:

| Avoid | Use instead |
|---|---|
| utilize | use |
| commence | start |
| terminate | stop / end |
| endeavour | try |
| facilitate | help / allow |
| implement | do / apply / install |
| leverage | use |
| subsequently | then / after |
| prior to | before |
| in order to | to |
| ensure | make sure |
| obtain | get |
| provide | give |
| approximately | about |
| sufficient | enough |
| additional | more |
| require | need |
| indicate | show |
| demonstrate | show |
| assist | help |
| perform | do |
| regarding | about |
| in the event that | if |
| at this point in time | now |
| due to the fact that | because |
| it is recommended that | you must / you should |

In **relax mode**, skip this table. Allow any word that is clear and unambiguous.

### 4. Paragraphs and Lists

- Maximum **6 sentences** per paragraph.
- Use numbered lists for sequential steps.
- Use bulleted lists for non-sequential items.
- Do not use more than **two levels** of nesting in a list.

### 5. Noun Clusters

- Do not use more than **3 nouns in a row** as a compound modifier.
- Break the cluster apart.

Not correct:

> "system pressure valve control unit"

Correct:

> "control unit for the system pressure valve"

### 6. Warnings and Cautions

- Write warnings and cautions **before** the step they relate to.
- Use the exact format:

```text
WARNING: [consequence of not following the instruction]

CAUTION: [risk of equipment damage]

NOTE: [additional helpful information]