---
title: "CSS Surface Morphing with anchor() and @starting-style"
anchor: "How to animate/popover surfaces using CSS anchor positioning and starting style transitions"
tags: [css, anchor-positioning, starting-style, surface-morphing, animation, popover, css-tricks]
description: "CSS techniques for morphing surfaces using anchor() positioning and @starting-style for smooth transitions"
source_url: "https://x.com/jh3yy/status/2014812951564243243"
---

## Reference

### Summary
Modern CSS enables surface morphing and smooth transitions for anchored elements using two key features:
- **`anchor()` function** - Position elements relative to anchor points
- **`@starting-style`** - Define starting styles for smooth entry animations

### anchor() Function
The `anchor()` function positions an element relative to a designated anchor element.

```css
/* Declare an anchor */
#anchor-element {
  anchor-name: --my-anchor;
}

/* Position popover relative to anchor */
#popover {
  position-anchor: --my-anchor;
  top: anchor(--my-anchor bottom);
  left: anchor(--my-anchor right);
}

/* Or use position-area */
#popover {
  position-anchor: --my-anchor;
  position-area: bottom;
  transform: translateX(50%);
}
```

### @starting-style for Smooth Transitions
To animate discrete properties like `display` and `opacity` for popovers:

```css
[popover] {
  display: none;
  opacity: 0;
  transition:
    opacity 500ms,
    display 500ms allow-discrete,
    overlay 500ms allow-discrete;

  &:popover-open {
    display: block;
    opacity: 1;

    @starting-style {
      opacity: 0;
    }
  }
}
```

### Key Concepts
1. **Anchor Name**: Declare with `anchor-name: --identifier`
2. **Position Anchor**: Reference with `position-anchor: --identifier`
3. **anchor() function**: Get position from anchor (`anchor(--name side)`)
4. **position-area**: Simplified axis-based positioning
5. **@starting-style**: Defines initial state for entry transitions
6. **transition-behavior: allow-discrete**: Required for discrete property transitions
7. **overlay**: Must be transitioned for top-layer elements

### Popover API + Anchor Combo
```html
<button popovertarget="my-popover">Open</button>
<div id="anchor-element" popover="auto" anchor-name="--my-anchor">
  Popover content
</div>
```

### Why This Combination Works
- **anchor()** handles the positioning logic (no JS needed)
- **@starting-style** enables smooth entry animations
- **Popover API** provides accessibility and top-layer rendering
- All three together create morphing surfaces without JavaScript

### Resources
- **MDN anchor()**: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/anchor
- **MDN Anchor Positioning**: https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using
- **CSS-Tricks Anchor Menu**: https://css-tricks.com/fancy-menu-navigation-using-anchor-positioning/
- **Chrome Blog (entry/exit animations)**: https://developer.chrome.com/blog/entry-exit-animations

### Use Cases
- Nested navigation menus
- Tooltips and popovers
- Morphing card surfaces
- Accessible dropdown menus
- Interactive UI panels
