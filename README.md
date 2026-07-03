# Codex Video Skills

This repository contains three production-focused Codex skills for AI video creation workflows:

- `screenwriter`: collaborative screenplay and story-structure development
- `shotlist-builder`: shot breakdown, blocking, and production review outputs
- `ai-video-prompt-optimizer`: multi-model video prompt packaging with bilingual output support

## Repository Scope

Only reusable skill files are included here.

Excluded on purpose:

- test outputs
- preview HTML files
- generated images
- temporary review artifacts
- local `outputs/` work products

## Structure

```text
skills/
  ai-video-prompt-optimizer/
  screenwriter/
  shotlist-builder/
```

## Notes

These skills are organized to support both:

- standalone use of a single module
- linked workflow use across screenplay -> shotlist -> prompt generation
