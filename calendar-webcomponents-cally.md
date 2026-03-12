---
title: Cally - Calendar WebComponents
anchor: Lightweight, temporal-based calendar WebComponents for custom date pickers
tags: [web-components, javascript, calendar, temporal, ui-components, open-source]
description: Small (<9KB), feature-rich calendar WebComponents built on the Temporal API
source_url: https://wicky.nillia.ms/cally/
---

## Reference

### Summary
Cally is a set of lightweight calendar WebComponents (<9KB min/gzip) built on the Temporal API. It provides low-level building blocks (calendar-date, calendar-range, calendar-multi, calendar-month) rather than a full date picker, allowing developers to use their own inputs, buttons, and popovers.

### Key Features
- **Small bundle**: <9KB min/gzip
- **Feature-rich**: Single dates, multiple dates, ranges, multi-month display
- **Framework-independent**: Plain HTML-friendly
- **Accessible**: Keyboard and screen reader support
- **Localizable**: Uses Intl.DateTimeFormat, CSS logical properties, RTL support
- **Themeable**: CSS parts and custom properties
- **Minimal dependencies**: Only one (Temporal polyfill)

### Components
- `<calendar-date>` - Single date selection
- `<calendar-range>` - Date range selection  
- `<calendar-multi>` - Multiple dates
- `<calendar-month>` - Month display (used inside other components)

### Installation
```html
<script type="module" src="https://unpkg.com/cally"></script>
```
or `npm install cally`

### Usage Example
```html
<calendar-range months="2">
  <calendar-month></calendar-month>
  <calendar-month offset="1"></calendar-month>
</calendar-range>
```

### Related
- GitHub: https://github.com/WickyNilliams/cally
- Spiritual successor to Duet date picker
- Inspired by React ARIA Components date/time
