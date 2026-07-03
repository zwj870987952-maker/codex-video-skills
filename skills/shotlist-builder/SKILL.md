---
name: shotlist-builder
description: Build production-ready cinematic shotlists, blocking plans, prompt blocks, and production HTML from screenplay material. Use when the user wants a shot breakdown, scene blocking, lens plan, prompt-sheet structure, Seedance-style shot plan, or production HTML for one or more scenes. Supports standalone use from a script or story summary, and pipeline use after screenplay creation.
---

# Shotlist Builder

This skill is the directing and cinematography module in a director-console workflow. Preserve the screenplay as story truth, then convert it into visual beats, blocking, and prompt-ready shot structure.

## Operating Modes

- `standalone`: use when the skill is called by itself from a script, treatment, or story summary.
- `pipeline`: use when screenplay output already exists upstream. In this mode, do not rewrite story facts; only translate them into shot design.

## Collaboration Loop

Before locking a shotlist:

- summarize what the script already establishes
- identify unresolved visual decisions
- explain why they matter
- let the user answer or explicitly skip

Use:

- `Known`
- `Missing`
- `Why it matters`
- `Reply or skip`

If the user skips, proceed with explicit directing assumptions.

## Core Flow

### Phase 1. Read the story input

Identify:

- scene boundaries
- character presence
- location logic
- prop logic
- action beats
- reveal beat

### Phase 2. Visual gap check

Before requesting assets or finalizing shots, tell the user:

- which characters need visual definition
- which locations need references
- which props need references
- which blocking decisions remain unresolved

Allow the user to answer, upload assets, or skip.

### Phase 3. Asset and blocking confirmation

Request only the assets that matter.

For scenes with multiple characters or critical prop geography:

- confirm approximate positions
- confirm eyelines
- confirm prop or reveal placement

If the user skips blocking, proceed with a labeled default layout.

### Phase 4. Build the shotlist

Convert screenplay beats into:

- shot purpose
- framing
- camera movement
- blocking
- prop interaction
- prompt-block grouping

## Read These References As Needed

- `reference/STYLE_BLOCK.md`
- `reference/PROMPT_PATTERNS.md`
- `reference/CAMERA_EMOTION.md`
- `reference/MICRO_BEATS.md`
- `reference/SPATIAL_BLOCKING.md`
- `reference/PROMPT_DENSITY.md`
- `reference/PLAN_TYPES.md`
- `templates/HTML_TEMPLATE.md`

## Core Directing Rules

- Clarify generic emotions into visible behavior.
- Maintain stable scene geography.
- Ask before assuming ambiguous asset mapping.
- Use blocking before prompting when multi-character space matters.
- Keep the background active and specific when the location is populated.
- Use practical-lighting logic and grounded camera behavior unless the user wants another style.

## Pipeline Guardrails

In `pipeline` mode, do not:

- add story events
- remove story events
- change who acts versus who observes
- change the reveal object
- change the reveal function

If the screenplay is too vague to shotlist safely, stop and ask or let the user skip with assumptions.

## Output Types

### Review shotlist

Use when the user wants to inspect logic first:

- shot-by-shot breakdown
- blocking assumptions
- asset list
- prompt-block grouping

### Production shotlist

Use when the user wants a usable artifact:

- structured shotlist
- prompt blocks
- blocking notes
- asset mapping
- production HTML if requested

## Handoff To Prompt Module

When prompts will be generated downstream, provide:

- shot ids
- beat ids
- prompt-block grouping
- role mapping
- asset usage
- blocking summary
- camera intent
- reveal shot id
- locked continuity constraints
- assumptions made after skips
