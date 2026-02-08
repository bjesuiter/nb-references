---
title: Kevin Powell - Border Radius Shapes Trick
anchor: CSS border-radius tricks for creating interesting/unique shapes beyond basic rounded corners
tags: [css, border-radius, shapes, web-design, css-tricks]
description: Kevin Powell YouTube short demonstrating border-radius tricks for making unique shapes
source_url: https://youtube.com/shorts/vVJlC1rBU4E
---

## Reference

### Summary
Kevin Powell demonstrates CSS border-radius tricks for creating interesting shapes beyond basic rounded corners. The video covers creative uses of border-radius values to make unique geometric shapes.

### Related Content
- Related video (Strange shapes with border-radius): https://youtube.com/shorts/ihL8vd__AMA
- Code examples: https://codepen.io/kevinpowell/

### Key Concept
Border-radius can take multiple values (slash-separated) to create elliptical corners:
```css
/* Single value - all corners same */
border-radius: 20px;

/* Multiple values - top-left top-right bottom-right bottom-left */
border-radius: 10px 30px 10px 30px;

/* Elliptical corners: horizontal / vertical radius */
border-radius: 50px / 30px;

/* Complex shapes with multiple values */
border-radius: 10px 20px 30px 40px / 20px 30px 40px 50px;
```
