# Prompt Package Template

Use this template for full commercial or multi-asset creation packages. Keep sections concise when the user's request is simple.

Default language policy:

- Chinese for review, planning, assumptions, and iteration notes
- English for the main copy-paste prompt
- add a Chinese prompt variant when the workflow benefits from it or the user asks for one

## 1. Creative Brief

Write this section in Chinese.

- Goal:
- Audience:
- Platform / aspect ratio / duration:
- Core selling point or narrative objective:
- Visual direction:
- Success criteria:

## 2. Assumptions And Missing Inputs

Write this section in Chinese.

List the important missing details.

If assumptions were made:

- make them explicit
- keep them easy to revise

## 3. Asset Inventory

Write this section in Chinese.

For each asset, capture:

- Asset type: image, video, product, character, logo, music, copy, reference link, style reference
- Intended use: hero subject, background, style reference, transition, voiceover, text overlay, ending frame, first frame
- Must keep: identity, product shape, color, material, logo, packaging, outfit, expression, composition, claim
- Changeable elements: background, camera, lighting, pose, motion, weather, props, edit pace
- Forbidden changes: identity drift, logo distortion, product mutation, wrong text, extra limbs/fingers, altered packaging
- Applicable shots: shot number, beat number, or full-video usage

## 4. Shot / Beat Structure

Write this section in Chinese.

Use 3-5 beats for most short videos:

1. Hook: first visual and motion that stop the scroll.
2. Establish: subject, product, world, or problem.
3. Action / transformation: the main movement, benefit, or narrative shift.
4. Proof / detail: close-up, texture, feature, expression, or result.
5. End frame: clean product shot, brand lockup, CTA space, or emotional finish.

## 5. English Model-Ready Prompt

Write as one coherent prompt:

```text
Create a [duration] [aspect ratio] video for [platform/use case].
Subject and assets: [asset-specific preservation instructions].
Scene: [setting, time, environment, key objects].
Action and temporal order: [beat-by-beat action].
Camera and motion: [shot size, lens feel, movement, transitions].
Visual style: [lighting, color, texture, realism/stylization].
Audio/text intent: [voice/music/text overlay instructions].
Quality constraints: [continuity, identity/product fidelity, no unwanted artifacts].
```

## 6. Chinese Prompt Variant

Provide this section when:

- the user asks for Chinese output
- the workflow is Chinese-first
- the target model community commonly uses Chinese prompts

Rewrite naturally in Chinese instead of translating word-for-word.

## 7. Negative Prompt / Avoid List

Include only relevant constraints:

```text
Avoid identity drift, product shape changes, distorted logo, unreadable or incorrect text, extra limbs, warped hands, flicker, unstable camera, abrupt scene changes, low-resolution details, overexposure, oversaturation, plastic skin, duplicated objects, watermark, subtitles unless requested.
```

## 8. Parameter Suggestions

Provide only parameters the model or UI likely exposes. If uncertain, phrase them as suggestions:

- Duration:
- Aspect ratio:
- Resolution / quality:
- Input mode:
- Reference strength or consistency:
- Camera / motion intensity:

## 9. Short Prompt Variant

Compress to one paragraph while preserving:

- assets
- action
- camera
- style
- key constraints

## 10. Iteration Notes

Write this section in Chinese.

- Identity drifts: strengthen asset preservation wording and reduce scene complexity.
- Product mutates: describe fixed geometry, material, logo placement, and packaging constraints earlier.
- Motion is weak: use one primary action verb and a clearer camera path.
- Text is wrong: remove generated text and reserve negative space for post-production overlay.
- Pacing is slow: reduce beats and specify the hook in the first second.
- Style is off: replace broad labels with concrete lighting, lens, color, and texture cues.
