---
title: Text Zoom Observer Element - Web Component for Zoom Detection
anchor: Web component to detect and react to browser text zoom / base font size changes
tags: [web-component, javascript, accessibility, zoom, text-size, custom-element]
description: Custom element that observes browser text zoom and exposes state via CSS :has() selector
source_url: https://github.com/knowler/text-zoom-observer-element
---

## My Reference

### Summary
A lightweight web component (`<text-zoom-observer>`) that detects when the browser's text zoom is greater than the base font size (assumed 16px) and exposes the state via CSS `:has()` selector.

### Installation

```html
<!-- Load the script -->
<script src="/path/to/text-zoom-observer-element.js"></script>

<!-- Add the element -->
<text-zoom-observer></text-zoom-observer>
```

### Usage

```css
/* Text is zoomed */
:root:has(text-zoom-observer:state(zoomed)) {
  background-color: DeepPink;
}

/* Or use for responsive adjustments */
:root:has(text-zoom-observer:state(zoomed)) {
  --adjusted-spacing: 1.2rem;
}
```

### Features

- **Lightweight custom element** - Minimal footprint
- **CSS :has() integration** - No JS event listeners needed
- **Zoom state detection** - Detects text zoom > 100%

### Limitations

- Assumes base font-size of 16px
- `:has()` selector may have performance implications
- Works best when you haven't changed document font-size

### Resources

- **GitHub:** https://github.com/knowler/text-zoom-observer-element
