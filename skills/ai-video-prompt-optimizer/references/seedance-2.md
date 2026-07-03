# Seedance 2.0 Reference

Use this reference when the user selects `Seedance 2.0`, `Seedance fast`, `Dreamina`, `Jimeng`, or adjacent Doubao-style video tools that follow a similar prompt style.

This reference is a model-specific layer inside `ai-video-prompt-optimizer`. It should improve the final prompt, not replace the shared workflow.

## What This Reference Is Good At

The Seedance 2.0 material is strongest in these areas:

- scene archetype routing
- motion and continuity awareness
- camera and cut discipline
- concrete action phrasing
- preventing vague emotional language

These are worth preserving and emphasizing.

## What To Fix Or Avoid

Do not inherit these traits from a raw Seedance-only skill without adjustment:

- JSON-only output as a hard default
- English-only interaction
- overly rigid API behavior when the user really wants a collaborative prompt package
- replacing the shared optimizer workflow with a model-specific workflow

Inside this skill, the optimized behavior is:

- process in Chinese
- final delivery defaults to bilingual
- use Seedance rules as prompt strategy, not as the entire UX

## How To Apply This Reference

Keep the shared optimizer flow:

1. clarify the brief and asset role
2. build the asset inventory
3. classify the scene
4. write the package
5. apply Seedance-specific constraints and fixes

## Default Output Policy For Seedance Requests

Unless the user asks otherwise:

- ask questions in Chinese
- explain assumptions in Chinese
- output the main copy-paste prompt in English
- also provide a Chinese prompt variant

If the user explicitly wants:

- prompt only
- JSON
- English only
- Chinese only

then switch to that format.

## Seedance Prompt Priorities

Optimize for:

- subject identity fidelity
- spatial clarity
- temporal continuity
- one dominant action flow
- one dominant camera logic per shot or beat
- concrete visible details over abstract adjectives

Seedance performs best when the prompt describes what the camera can see and how motion unfolds over time.

## Asset Handling

Before writing the final prompt, track:

- Characters: appearance, clothing, distinguishing features, role in scene
- Locations: interior/exterior, architecture, lighting sources, atmosphere
- Props: objects that appear, move, break, get held, or become focal points
- Brand/product details: logo placement, geometry, label text, packaging, material
- Reference images/videos: whether each asset is hero subject, style reference, background reference, first frame, or ending frame

Never invent named characters or branded product details that the user did not provide.

## Scene Router

Classify the scene before drafting.

### Action

Use when the scene is driven by:

- pursuit
- combat
- impact
- stunts
- escape
- collision
- attack or defense

Preferred phrasing:

- intent + named move
- force + direction
- visible contact result

Good:

- "a spinning back kick connects and drives him into the car door"
- "she lunges forward, grabs the briefcase, and pivots toward the exit"

Avoid:

- joint-by-joint biomechanics
- impossible multi-step choreography in one continuous beat

### Dialogue

Use when the scene is driven by:

- confrontation
- negotiation
- interrogation
- confession
- restrained emotional exchange

Focus on:

- power shifts
- pauses
- reactions
- eye-line changes
- posture changes
- restrained camera behavior

If the user provides too much dialogue for a short clip, keep:

- the setup line
- the turning-point line
- the reaction line

Convert the rest into physical behavior.

### General / Atmosphere / Journey / Reveal

Use when the scene is mainly about:

- mood
- movement through space
- unveiling something hidden

Useful sub-modes:

- journey: subject moving through space
- atmosphere: almost-static mood shot with subtle changes
- reveal: camera controls when the key subject becomes visible

## Engine Rules

These are the most important Seedance-specific constraints.

- Describe visible physics, not abstract outcomes.
- Use one dominant subject action at a time.
- Use one dominant camera move at a time.
- Re-anchor positions after cuts.
- Keep scene geography stable across the prompt.
- Do not rely on reflections for important story information.
- Do not describe off-screen events as if the model can infer them.
- If a character exits frame, treat that beat as an implicit transition unless the next beat clearly resets the shot.
- Track no more than 2-3 important agents in one prompt block when fidelity matters.

## Camera And Cut Rules

### Double contrast

When describing multiple cuts, each cut should change both:

- shot size
- camera character

Examples:

- wide tracking to close static
- low handheld medium to high-angle locked wide
- medium push-in to extreme close-up insert

Avoid repeating nearly the same framing and movement across every cut.

### Re-anchoring

After a cut back into established space, restate:

- who is where
- who faces whom
- movement direction

This improves continuity.

### Inserts

Use inserts only when they are causally motivated.

Good:

- "close-up of Lin's thumb tightening around the phone edge"
- "insert of the bottle label as water runs down the glass"

Avoid decorative inserts with no narrative reason.

## Language Rules For Final Prompts

- Present tense
- Active voice
- Concrete visual language
- Keep critical fidelity constraints close to the relevant subject
- Avoid vague hype words

Prefer:

- subject
- location
- action
- camera
- lighting
- style
- continuity constraints

Instead of broad mood-only prompting.

## Recommended Prompt Structure

Use this structure for the main English prompt:

```text
Generate a [duration], [aspect ratio] Seedance 2.0 video.
Reference preservation: [what must stay consistent from assets].
Main subject: [character/product/hero visual description].
Scene and atmosphere: [location, time, weather, lighting, palette].
Action flow: [opening beat, middle beat, ending beat].
Camera plan: [shot size, lens feel, movement, framing logic].
Visual style: [realistic/commercial/cinematic/etc. with concrete texture].
Audio or text intent: [dialogue, music, silence, or leave clean space for text overlay].
Continuity constraints: [identity, geometry, logo, prop placement, motion consistency, artifact avoidance].
```

For the Chinese prompt variant:

- rewrite natively
- do not translate mechanically
- keep the same action logic and continuity constraints

## Common Fixes

If identity drifts:

- repeat the exact identity details in the first two lines
- simplify background action
- reduce the number of active subjects

If product geometry mutates:

- restate shape, material, logo placement, and label behavior
- say "no redesign of packaging or logo"

If motion becomes chaotic:

- reduce to one action and one camera move
- shorten the action chain

If references are ignored:

- state each asset's role explicitly
- say whether it is hero subject, first frame, background, or style reference

If pacing feels flat:

- define a stronger first-second hook
- define a more intentional ending frame

If text renders poorly:

- instruct the model to leave clean composition space
- add text in post unless the user specifically needs in-video generated text

## Parameter Suggestions

Only mention settings the UI likely exposes.

- Duration: usually 5-8 seconds for a compact beat unless the brief says otherwise
- Aspect ratio: `9:16` for vertical short video, `16:9` for landscape, `1:1` for square social
- Input mode: text-to-video with no assets, image-to-video or reference-guided when fidelity matters
- Reference strength: increase for brand/product/character fidelity, lower for looser transformations
- Motion intensity: moderate for product and branding, higher for action or dance

## Anti-Slop Reminder

Avoid empty adjectives such as:

- breathtaking
- mesmerizing
- beautifully crafted
- cinematic masterpiece
- rich tapestry
- next-level

Replace them with concrete visible direction.
