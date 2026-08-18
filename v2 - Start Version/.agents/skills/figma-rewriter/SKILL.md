---
name: rewriter
description: Analyze and rewrite text on Figma layers. Trigger on "/word", "/word help", "/word jargon", "/word font", "/word spelling", "/word seo", "/word cro", "/word cta", "/word story", "/word version", "/word tone", "/word shorter", "/word longer", "/word [number]" (e.g. "/word 12" or "/word shorter 10"), "/word consistency", "/word placeholder", or "/word [language]" (e.g. "/word spanish"). Use whenever the user wants to audit Figma copy for jargon, grammar/spelling, or font properties (family/weight/size), get SEO/CRO/CTA/storytelling/tone rewrite suggestions (individually or combined via /word version), rewrite copy to a target word count, tighten or expand copy for length, flag inconsistent terminology, replace placeholder/lorem-ipsum text, or translate selected Figma text layers. Requires a connected Figma MCP/plugin tool that can read text layer content from the current selection — if none connected, say so and stop (except when explaining what /word does).
---

# /word

Text analysis and rewriting for Figma text layers, scoped to the **current selection** only.

## Setup check

Before running any subcommand, confirm a Figma MCP/plugin tool is connected and can read layer content. If not, tell the user and stop.

If nothing is selected in Figma, do NOT fall back to the page — stop and ask the user to select the text layer(s) they want to work on.

## Reading selected text

For all subcommands, first read the text content of every text layer in the current selection via the Figma tool. Keep a mapping of layer id → text so results can reference specific layers. For `/word font`, also read each layer's style properties (font family, weight, size) rather than relying on text content alone.

## Subcommands

### /word help
List all subcommands with a one-line description each. No Figma connection or selection required — answer directly, don't run the setup check.

- `/word jargon` — list jargon/buzzwords in selection (read-only)
- `/word font` — list font family, weight, and size used in selection (read-only)
- `/word spelling` — flag grammar and spelling issues (read-only)
- `/word seo` — suggest SEO rewrites (read-only)
- `/word cro` — suggest CRO rewrites (read-only)
- `/word cta` — clarify button/CTA text using surrounding context (read-only)
- `/word story` — suggest storytelling rewrites (read-only)
- `/word version` — show SEO, CRO, and story suggestions together, pick which to apply (read-only)
- `/word tone [target]` — rewrite to match a target tone (read-only)
- `/word shorter [number]` — suggest tightened rewrites, optionally to an exact word count (read-only)
- `/word longer [number]` — suggest expanded rewrites, optionally to an exact word count (read-only)
- `/word [number]` — rewrite to an exact word count (read-only)
- `/word consistency` — flag inconsistent terminology across selection (read-only)
- `/word [language]` — translate selection to target language (read-only)
- `/word placeholder` — replace placeholder text using attached file or inferred context (writes to layers, confirmation required)
- `/word help` — show this list

All are **read-only / chat-only** (report in chat, never write to layers) EXCEPT `/word placeholder`.

### /word jargon
List all jargon, buzzwords, and unclear technical terms found in the selected text. For each: the term, which layer it's in, and a plain-language one-line explanation of what it means. Present as a list, grouped by layer.

### /word font
List the font family, font weight, and font size for every text layer in the selection, read via the Figma tool's style properties (not inferred from content). Present as a table: Layer | Font Family | Weight | Size. If a layer has mixed styles within itself (multiple fonts/sizes in one text node), note that explicitly rather than picking one value. Chat only.

### /word spelling
Check the selected text for grammar and spelling issues. For each layer with issues: show original vs. corrected text, with the specific error(s) noted (e.g. "subject-verb agreement", "misspelled 'recieve'"). If no issues found in a layer, skip it — don't list clean layers. Chat only.

### /word seo
Suggest SEO-improved rewrites of the selected text (keyword clarity, scannability, natural language search intent). For each layer: show original vs. suggested rewrite, and a one-line rationale. Chat only — do not write to layers.

### /word cro
Suggest CRO (conversion rate optimization) rewrites — clearer CTAs, urgency/value framing, friction reduction. Same format: original vs. suggested, with rationale. Chat only.

### /word cta
Read the button/CTA text in the selection along with surrounding context (parent frame, nearby headline/body copy, destination implied by the flow) to understand what the action actually does. Rewrite each CTA to be clearer and more actionable — specific verb, concrete outcome, no vague labels like "Click here" or "Submit". For each: original vs. suggested, with a one-line rationale grounded in the surrounding context. Chat only.

### /word story
Suggest rewrites that improve storytelling — narrative flow, emotional resonance, better hook/arc. Same format: original vs. suggested, with rationale. Chat only.

### /word version
Run SEO, CRO, and story suggestions together in a single pass over the selection. For each layer, show all three suggested rewrites side by side (or stacked, labeled SEO / CRO / Story) with original text for comparison. Then ask the user which version(s) they'd like to apply per layer — this command itself never writes to layers. If the user picks a version to apply, that's a separate write action requiring its own confirmation (same as `/word placeholder`'s confirm-before-write pattern) since none of SEO/CRO/story normally write to layers.

### /word tone [target]
Rewrite the selected text to match a target tone (e.g. "playful", "formal", "technical", "friendly"). If no target is given, ask which tone before proceeding. For each layer: original vs. suggested rewrite, and a one-line rationale for how it shifts tone. Chat only.

### /word shorter [number] / /word longer [number]
Suggest tightened (`shorter`) or expanded (`longer`) rewrites of the selected text. Without a number, just tighten/expand naturally. With a number (e.g. `/word shorter 10`, `/word longer 25`), rewrite to hit that exact word count as closely as possible. For each layer: original, suggested rewrite, and word count for both so the user can judge fit. Chat only.

### /word [number]
A bare number (e.g. `/word 12`) rewrites each selected layer's text to that exact word count, without a length direction implied — condense or expand as needed to land on the target. For each layer: original, suggested rewrite, word count for both. Chat only.

### /word consistency
Scan the selected text layers for inconsistent terminology — e.g. "Sign in" vs "Log in", "Cancel" vs "Dismiss" used for the same action. Group findings by term-cluster: list the variants found, which layers each appears on, and suggest one term to standardize on. Chat only.

### /word [target language]
Any argument not matching a known subcommand and not a plain number is treated as a target language (e.g. "spanish", "japanese", "fr"). Translate each selected text layer's content into that language. Show layer → original → translation. Chat only — do not write to layers, even though this looks like a replacement task.

### /word placeholder
Replace placeholder/lorem-ipsum/dummy text in the selection with real copy. This is the only subcommand that writes to layers, and it always requires confirmation first.

1. **If a file is attached**: read it and use its content as the source material for replacement text. Skip to step 4.
2. **If no file is attached**: ask the user what context to use to write the copy (e.g. product description, target audience, tone, key message). Wait for their answer.
3. **If the user has no context to give**: infer appropriate replacement text from the surrounding context — sibling layers, parent frame/component name, nearby real copy, component structure. For each placeholder layer, generate 3 distinct suggestions and present them so the user can pick which one to use per layer.
4. Build the proposed replacement for each placeholder layer: layer → current (placeholder) text → proposed text (the file-derived text, the user-context-derived text, or the suggestion the user picked in step 3).
5. Show the full proposed replacement list to the user and ask for confirmation before writing anything.
6. Only after explicit user confirmation, write the approved replacements back to the layers via the Figma tool.
7. If the user requests changes, revise and re-confirm before writing.

## Output formatting

For all read-only subcommands, present results as a simple table or list: Layer | Original | Suggestion/Finding | Note. Keep rationale to one line per item — this is a scan/suggestion tool, not a long-form report.
