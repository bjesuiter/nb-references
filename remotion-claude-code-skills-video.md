---
title: Claude Code + Remotion Skills Video - Gist
anchor: Example of using AI agents (Claude Code) with Remotion to create videos - full workflow gist
tags: [remotion, video, ai-agent, claude-code, animation, react, typescript]
description: GitHub gist showing Claude Code creating a Remotion skills announcement video with terminal animations, 3D transforms, and logo compositions
source_url: https://gist.github.com/JonnyBurger/5b801182176f1b76447901fbeb5a84ac
---

## Summary

A complete GitHub gist showing how **Claude Code** (AI agent) used **Remotion** to create a polished video for the "Agent Skills" announcement. Demonstrates AI-assisted video creation workflow.

## What It Shows

The gist documents the full workflow where Claude Code:
1. **Created a macOS terminal composition** — 1280x1000px terminal with light theme
2. **Added typewriter animation** — Types "npx skills add remotion-dev/skills"
3. **Created ASCII art + output animation** — Shows installation output with staggered lines
4. **Built a logo composition** — Remotion + Claude Code + OpenCode logos with "+" separators
5. **Added 3D transforms** — Rotate X/Y, perspective, spring animations
6. **Implemented flip transition** — Terminal flips toward camera on exit
7. **Rendered final video** — Exported to MP4

## Key Techniques Demonstrated

| Technique | Implementation |
|-----------|---------------|
| **Typewriter effect** | `interpolate()` with `charsPerSecond` timing |
| **Staggered lines** | `framesPerLine` interpolation per line |
| **Spring animations** | `spring()` from Remotion with damping/stiffness |
| **3D rotation** | `rotateX()`, `rotateY()` with `perspective` |
| **Flip transition** | Wrapper div with `transform-origin: bottom` + `rotateX()` |
| **Series composition** | Sequential animations with `Series.Sequence` |
| **Logo overlay** | `<Img src={staticFile(...)} />` |

## Code Patterns Used

### Typewriter Animation
```tsx
const charsPerSecond = 15;
const visibleChars = interpolate(frame, [0, command.length * framesPerChar], [0, command.length]);
const displayedText = command.slice(0, visibleChars);
```

### Spring Animation (No Bounce)
```tsx
const slideIn = spring({
  frame,
  fps,
  config: { damping: 200, stiffness: 100 },
});
const translateY = interpolate(slideIn, [0, 1], [700, 0]);
```

### 3D Flip Transition
```tsx
<div style={{ perspective: 1000 }}>
  <div style={{ transformOrigin: "center bottom", transform: `rotateX(${flipRotateX}deg)` }}>
    <MacTerminal />
  </div>
</div>
```

## For Skills Integration

This pattern is perfect for **agent skills** that create videos:

1. **Create composition skill** — Template for common video types
2. **Text-to-video skill** — Convert script to Remotion animation
3. **Render skill** — Export MP4/GIF from compositions
4. **Logo compositing skill** — Combine logos/branding

## Related Skills to Build

- `remotion-animation` — Reusable Remotion patterns
- `remotion-logo-combo` — Logo + text compositions
- `remotion-typewriter` — Typewriter text effects
- `remotion-3d-effects` — 3D transforms and transitions

## Links

- **Gist:** https://gist.github.com/JonnyBurger/5b801182176f1b76447901fbeb5a84ac
- **Remotion:** https://www.remotion.dev
- **Remotion GitHub:** https://github.com/remotion-dev/remotion
