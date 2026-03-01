---
title: Pinchtab - Headless Browser Fleet Orchestrator
anchor: When I need to manage multiple headless browser instances for scraping/automation
tags: [browser, orchestration, headless, puppeteer, playwright, automation, devtools]
description: Minimalist Node.js tool to launch and manage fleet of headless browser instances
source_url: https://www.opensourceprojects.dev/post/e7415816-a348-4936-b8bd-0c651c4ab2d8
---

## Summary

**Pinchtab** is a minimalist orchestrator for managing a fleet of headless browser instances. It solves the problem of spinning up, managing, and tearing down multiple browser instances for scraping, testing, or automation.

## Key Features

- **Fleet Management**: Launch N headless browser instances (Chrome/Chromium) with ports, PIDs, and WebSocket endpoints managed automatically
- **Minimalist & Decoupled**: Works with any tool that connects via DevTools Protocol (Puppeteer, Playwright, custom scripts)
- **Developer-Friendly**: Clean programmatic API + CLI
- **Perfect for**: Large-scale data extraction, load testing, parallel visual regression tests

## Quick Example

```javascript
const { Pinchtab } = require('pinchtab');
const orchestrator = new Pinchtab();

// Launch 3 headless Chrome instances
const fleet = await orchestrator.launch(3);

console.log(fleet); // connection info for each instance

// Gracefully shutdown
await orchestrator.destroy();
```

## Links

- GitHub: https://github.com/pinchtab/pinchtab
