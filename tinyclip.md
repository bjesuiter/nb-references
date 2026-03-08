---
title: TinyClip - Cross-Platform Clipboard Library
anchor: Quick access when needing a tiny clipboard utility for Node.js
tags: [nodejs, clipboard, library, cross-platform, utilities, tinylibs]
description: A tiny, cross-platform clipboard utility for Node.js - uses native OS clipboard functionality
source_url: https://github.com/tinylibs/tinyclip
---

## Reference

### Summary
A tiny, cross-platform clipboard library for Node.js. Uses native OS clipboard functionality.

### API
```javascript
import { readText, writeText } from 'tinyclip';

await writeText('hello world');
const text = await readText();
```

### Features
- Cross-platform (works on Windows, macOS, Linux)
- Native OS clipboard access
- Tiny footprint
- TypeScript support

### Note
In the browser, you can use the native Clipboard API instead of a dependency.

### Source
- GitHub: https://github.com/tinylibs/tinyclip
- npm: `npm install tinyclip`
- Part of tinylibs
