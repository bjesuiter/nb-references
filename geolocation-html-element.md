---
title: HTML <geolocation> Element - Chrome 144+
anchor: geolocation-html-element-chrome-144
tags: html, geolocation, chrome, web-api, progressive-enhancement
description: New declarative HTML element for location requests in Chrome 144+ (January 2026)
source_url: https://developer.chrome.com/blog/geolocation-html-element?hl=de
---

# HTML <geolocation> Element

Chrome 144+ (January 2026) introduces a new declarative HTML element for location requests.

## What It Does

- Replaces imperative `navigator.geolocation.getCurrentPosition()` calls
- User clicks browser-controlled button → clear intention
- Acts as data broker, not just permission broker
- Drastically reduces boilerplate code

## Attributes

```html
<geolocation 
  onlocation="handleLocation(event)"
  autolocate 
  accuracymode="precise"
  watch>
</geolocation>
```

| Attribute | Purpose |
|-----------|---------|
| `onlocation` | Event handler for location data |
| `autolocate` | Automatically request location on click |
| `accuracymode` | `"precise"` or `"coarse"` |
| `watch` | Continuously update location |

## Benefits

1. **Clear Intention** - User explicitly signals "I want to share my location"
2. **Simplified Recovery** - If previously blocked, user can click to restore permission
3. **Auto-refresh** - Clicking updates location without new prompt

## Progressive Enhancement

- **Fallback**: Browsers without support render child elements (fallback button)
- **Polyfill**: `geolocation-element-polyfill` available
- **Feature detection**: `HTMLGeolocationElement in window`

## Styling Constraints

- Minimum size requirements
- Contrast requirements
- No transparent elements (prevents misleading design)

## Browser Support

- Chrome 144+ (January 2026)
- Other browsers: Use polyfill or fallback content

## Example Usage

```html
<geolocation onlocation="handleLocation(event)" accuracymode="precise">
  <button>Share my location</button>
</geolocation>

<script>
  function handleLocation(event) {
    const { latitude, longitude, accuracy } = event.detail;
    console.log(latitude, longitude, accuracy);
  }
</script>
```
