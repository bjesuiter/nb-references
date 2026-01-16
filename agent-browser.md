---
title: Agent Browser - Lean Browser Automation CLI
anchor: lean browser automation cli alternative to playwright
tags: browser, automation, cli, rust, nodejs, playwright-alternative
description: Fast Rust-based headless browser automation CLI with Node.js fallback
source_url: https://github.com/vercel-labs/agent-browser
---

## My Reference

A lightweight headless browser automation tool that serves as a leaner alternative to Playwright. Available as a standalone CLI outside of Clawdbot.

### Key Features
- Rust-based with Node.js fallback for broad compatibility
- Commands: open, snapshot, click, fill, type, screenshot, navigate, and more
- Session management for multiple isolated browser instances
- AI-friendly workflow with JSON output and deterministic element refs (@e1, @e2, etc.)
- No extension relay required (unlike Clawdbot's chrome profile)

### Installation
```bash
npm install -g agent-browser
agent-browser install
```

### Quick Start
```bash
agent-browser open example.com
agent-browser snapshot
agent-browser click @e2
agent-browser fill @e3 "test@example.com"
agent-browser screenshot page.png
agent-browser close
```

### Notes
- Refs are stable per page load but change on navigation
- Use `fill` instead of `type` for input fields (clears existing text)
- Use `--headed` flag to see the browser window for debugging
- Use `--session <name>` for isolated browser instances
