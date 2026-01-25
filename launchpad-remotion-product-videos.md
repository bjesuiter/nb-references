---
title: Launchpad - Product Launch Videos with Remotion
anchor: React-based video creation tool for product launches using Remotion, Next.js, and TailwindCSS
tags: [remotion, video, product-launch, react, nextjs, tailwindcss, animation, claude-code]
description: Monorepo for creating product launch videos programmatically with React components
source_url: https://github.com/trycua/launchpad
---

## My Reference

### Summary

**Launchpad** is a monorepo for creating product launch videos using Remotion, Next.js, and TailwindCSS. Built for teams who want to make videos with React instead of traditional video editors. Works great with Claude Code + Remotion Skills.

### Content

## Quick Start

```bash
# Install dependencies
pnpm install

# Create a new video project
pnpm create-video

# Open Remotion Studio
pnpm remotion

# Render video
pnpm render
```

## Project Structure

```
launchpad/
├── packages/
│   ├── shared/      # Reusable components (FadeIn, SlideUp, TextReveal)
│   └── assets/      # Brand assets (colors, fonts, sounds)
├── videos/
│   ├── _template/   # Template for new videos
│   └── cuabench/    # Example video project
├── scripts/
│   └── create-video.ts  # CLI to scaffold new videos
└── docs/            # Documentation
```

## Packages

| Package | Description |
|---------|-------------|
| `@launchpad/shared` | Reusable Remotion components and hooks |
| `@launchpad/assets` | Brand colors, fonts, and sound effects |

## Example Video

The `videos/cuabench/` directory contains a complete example showing:
- Word-by-word text animations
- Terminal and code editor scenes
- Counter animations with easing
- Video transitions
- Sound effects and background music

```bash
pnpm --filter @launchpad/cuabench remotion
```

## Using with Claude Code

Install Remotion skills for AI-assisted video development:
```bash
npx skills add remotion-dev/skills
```

Then describe what you want:
> "Create an intro scene with word-by-word text reveal, white text on dark background"

## Commands

| Command | Description |
|---------|-------------|
| `pnpm create-video` | Create a new video project |
| `pnpm remotion` | Open Remotion Studio |
| `pnpm dev` | Start Next.js preview |
| `pnpm render` | Render video locally |
| `pnpm build` | Build all packages |

## Resources

- [Getting Started](docs/GETTING_STARTED.md)
- [Creating Videos](docs/CREATING_VIDEOS.md)
- [Shared Components](docs/SHARED_COMPONENTS.md)
- [Remotion Documentation](https://remotion.dev/docs)
