# AGENTS.md

This repository is a collection of reusable skills and instructions for AI coding/writing agents (e.g. GitHub Copilot). It has no build, test, or runtime — it is documentation consumed by agents at prompt time.

## Structure

| File/Directory | Purpose |
|---|---|
| `files_made/INSTRUCTION.md` | Global work guidelines |
| `files_made/MEMORY.md` | Global project memory and context |
| `files_made/GENERATE.md | Use when user ask to generate a screen |
| `files_made/PROJECT-SETTTING.md | Global storage of reusable variable |
| `.agents/skills/` | Container directory for all individual skills |


## Skills

| Skill | Trigger | Purpose |
|---|---|---|
| `ASD-STE100` | `/asd-ste100`, `/asd-ste100 relax` | Rewrite text to comply with ASD-STE100 Simplified Technical English. |
| `Caveman` | `/caveman`, "less tokens", "be brief" | Ultra-compressed responses (~75% token cut) at selectable levels. |
| `Humanizer` | requests to remove AI-sounding writing | Strips common AI-writing tells (em dashes, rule of three, filler phrases, etc.). |
| `I Have ADHD` | `/i-have-adhd` | Reshapes output for ADHD readability (lead with next action, numbered steps, visible wins); stays active until told to stop. |
