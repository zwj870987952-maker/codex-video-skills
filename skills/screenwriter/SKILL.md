---
name: screenwriter
description: Write and revise screenplay material for films, shorts, scenes, treatments, beat sheets, and screenplay structure. Use when the user wants to write a script, scene, treatment, story beats, dialogue, revise a screenplay, shorten pages, estimate screen time, or prepare screenplay material for downstream shotlisting. Supports standalone use and upstream pipeline use before shotlist and prompt creation.
---

# Screenwriter

This skill is the writing module in a director-console workflow. Keep the user involved in decisions, but preserve the core screenplay craft rules below.

## Operating Modes

- `standalone`: use when the skill is called by itself. Gather context directly, write scenes or treatments, and operate independently.
- `pipeline`: use when the user is creating across screenplay -> shotlist -> prompts. In this mode, screenplay output becomes the upstream source of truth for downstream modules.

## Collaboration Loop

Before writing a full scene, treatment, or beat sheet:

- summarize what is already known
- identify what is still missing
- explain why the missing information matters
- ask the user to reply or explicitly skip

Use a compact structure:

- `Known`
- `Missing`
- `Why it matters`
- `Reply or skip`

If the user skips, proceed with explicit assumptions instead of blocking.

## Read In This Order

Before substantial screenplay work, read:

1. `methodology.md`
2. `style-rules.md`
3. `workflow.md`
4. `timing-and-cutting.md`

Use tools only when needed:

- `tools/build_screenplay.js` for Hollywood-format `.docx`
- `tools/build_bilingual.js` for bilingual screenplay output
- `tools/build_treatment.js` for treatment-style output

Templates are available in `templates/` for synopsis, characters, worldbuilding, and treatment work.

## Core Writing Rules

- Write only what can be seen or heard on screen.
- Use active verbs and concise action lines.
- Do not write internal thoughts or novel-style prose.
- Do not silently overwrite user-provided canon.
- Give one strong version at a time instead of many parallel alternatives.
- If a version fails, ask one narrow follow-up question and revise.

## Decision Gates

Before locking a screenplay result, confirm or skip:

- protagonist of the scene
- objective of the scene
- source of tension
- key prop or reveal logic
- ending image

If the user wants speed, compress these into a short checklist and continue with labeled defaults when skipped.

## Output Types

### Exploratory output

Use when the story is still forming:

- short concept summary
- assumptions
- open decisions
- one proposed direction

### Scene output

Use when enough context exists for a real scene:

- slugline
- action lines
- dialogue if needed
- clear ending beat

### Pipeline handoff output

Use when downstream modules will consume the result. In addition to the screenplay text, provide:

- title
- logline
- scene summary
- character list
- location list
- prop list
- ordered scene beats
- reveal or ending beat
- locked facts
- assumptions made after user skips

## Pipeline Guardrails

In `pipeline` mode, downstream modules may stage and visualize the scene, but they should not change:

- protagonist identity
- observer or support roles
- prop function
- cause-and-effect order
- final reveal

If a screenplay revision changes any of these locked facts, call that out explicitly.
