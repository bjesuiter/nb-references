---
title: Interruptible Swiping Gestures on the Web
anchor: How to make swipe gestures that can be interrupted by user input
tags: [ui, gestures, web, interaction, ux, swipe]
description: Techniques and patterns for implementing swipe gestures that respond to user input mid-gesture
---

## What Are Interruptible Swiping Gestures?

Swipe gestures that can be "interrupted" or canceled if the user:
- Changes their mind mid-swipe
- Makes an unexpected movement
- Triggers a conflicting interaction

## Key Patterns

### 1. Touch/Mouse Event Handling
- Listen to `touchstart`/`mousedown`, `touchmove`/`mousemove`, `touchend`/`mouseup`
- Track velocity and direction
- Detect "interruption" signals (finger lift, secondary touch)

### 2. Visual Feedback
- Animate smoothly during the gesture
- Show "snap back" animation if interrupted
- Use CSS transitions for fluid feel

### 3. State Management
- Track gesture state: idle → dragging → committed → complete
- Store original position to snap back
- Debounce rapid changes

## Implementation Tips

- Use `requestAnimationFrame` for smooth updates
- Consider passive event listeners for performance
- Test on real devices (touch behavior differs from mouse)
- Handle edge cases: multi-touch, scrolling conflicts

## Related
- iOS/Android native gesture handling
- Libraries: Hammer.js, Interact.js
