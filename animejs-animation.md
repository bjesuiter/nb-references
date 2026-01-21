---
title: Anime.js - JavaScript Animation Library
anchor: Lightweight, flexible JS animation library with layout support
tags: [javascript, animation, animejs, ui, frontend, library]
description: Anime.js documentation for layout animations - lightweight flexible JS animation library
source_url: https://animejs.com/documentation/layout/
---

## Summary

**Anime.js** is a lightweight (~3KB gzipped) JavaScript animation library known for its flexibility and clean API. The documentation covers layout animations including grid and flexbox animations.

## Key Features

- **Lightweight** — ~3KB gzipped
- **Flexible** — Works with any CSS property, transform, colors
- **Timeline** — Sequence animations with built-in timeline
- **Staggering** — Stagger effects for grid/list animations
- **Path animation** — Animate along SVG paths

## Common Use Cases

- UI interactions and micro-animations
- Page transitions
- Loading animations
- Hover effects
- Scroll-triggered animations

## Example

```javascript
anime({
  targets: '.element',
  translateX: 250,
  rotate: '1turn',
  duration: 800,
  easing: 'easeInOutQuad'
});
```

## Related

- GSAP (more powerful, larger)
- Framer Motion (React-specific)
- CSS animations (native, less control)
