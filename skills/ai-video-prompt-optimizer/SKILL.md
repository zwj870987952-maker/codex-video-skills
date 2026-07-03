---
name: ai-video-prompt-optimizer
description: Optimize AI video prompts and reusable prompt packages from a user's goal, assets, shot design, and chosen model. Use when the user wants AI video prompts, prompt packages, Seedance 2.0 or Seedance-fast prompts, Dreamina/Jimeng/Doubao video prompts, image-to-video prompts, asset-to-video prompts, storyboard prompts, or model-specific video prompt optimization. Supports standalone use and downstream pipeline use after screenplay and shotlist creation.
---

# AI Video Prompt Optimizer

This skill is the prompt-strategy module in a director-console workflow. Keep the user involved in decisions, default to Chinese interaction, and output bilingual results unless the user asks otherwise.

## Default Interaction Style

- interact in Chinese
- check what is missing before final prompting
- let the user answer or explicitly skip
- label assumptions clearly
- output final results in Chinese + English by default

## Operating Modes

- `standalone`: derive prompt structure directly from a brief, concept, asset set, or one-shot request.
- `pipeline`: consume locked screenplay and shotlist outputs. In this mode, translate existing visual events into prompts instead of rewriting story logic.

## Missing-Info Loop

Before final prompting, check for:

- target model
- aspect ratio
- duration
- asset role
- reference availability
- prompt granularity
- desired output format
- must-keep fidelity constraints

Use:

- `Known`
- `Missing`
- `Why it matters`
- `Reply or skip`

If the user skips, proceed with labeled defaults.

## Model Routing

### Generic mode

Use when no model is chosen:

- stay model-agnostic
- mark model-specific settings as placeholders

### Seedance-family mode

Use when the user names:

- Seedance 2.0
- Seedance fast
- Dreamina
- Jimeng
- Doubao video

Read `references/seedance-2.md` and apply its action, continuity, and camera logic.

### Other named-model mode

- use the shared workflow
- avoid unsupported fake settings

## References And Templates

- `references/prompt-package-template.md` for full prompt-package shape
- `references/seedance-2.md` for Seedance-family prompting strategy

## Core Rules

- Keep prompts concrete: subject, environment, action, camera, lighting, texture, temporal order.
- Keep critical fidelity constraints close to the relevant subject or asset.
- When reference images or videos are provided, explain each reference's role.
- When the target workflow supports asset handles, output both:
  - a handle-ready version using mappings like `@image1`
  - a plain-text compatible version

## Pipeline Guardrails

In `pipeline` mode, do not:

- change screenplay story logic
- add new visual events outside the shotlist
- reassign character roles
- change the reveal object or reveal function

Each prompt block should map back to shot ids, beat ids, or prompt-block ids from the shotlist.

## Output Modes

### Full package

Use for reusable collaboration:

- Chinese brief
- assumptions
- asset inventory
- shot or beat summary
- English main prompt
- Chinese prompt variant
- negative constraints
- parameter suggestions
- iteration notes

### Compact package

Use for fast review:

- short Chinese summary
- English main prompt
- Chinese prompt variant if useful
- avoid list

### Raw prompt mode

Use only when the user explicitly wants:

- prompt only
- JSON payload
- direct model input
