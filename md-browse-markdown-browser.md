---
title: "md-browse — Markdown Browser"
anchor: "View websites like an AI does (markdown-first browser that converts HTML to clean markdown)"
tags: [browser, markdown, ai, web, tool, electrobun]
description: "Markdown-first browser that prioritizes markdown content and converts HTML to clean markdown similar to what AI tools see"
source_url: "https://github.com/needle-tools/md-browse"
---

## Reference

### Summary
md-browse is a markdown-first browser built with Electrobun. It prioritizes markdown content when fetching web pages and converts HTML to clean markdown similar to what AI tools (Copilot, Claude, etc.) see.

**Problem Solved:**
See exactly what AI models see when they scrape websites — useful for debugging RAG pipelines, verifying AI-generated content, or simply browsing without clutter.

### Features
- **Markdown-First** — Sends `Accept: text/markdown` headers first; displays native markdown when available
- **HTML to Markdown** — Converts HTML pages to clean, readable markdown using Turndown, tuned to match AI output
- **Dual View Mode** — Toggle between raw markdown and rendered preview
- **Tab Support** — Multiple tabs with navigation history (back/forward)
- **Clean Design** — Dark, modern UI focused on readability

### How It Works
1. Enter a URL
2. Fetches with `Accept: text/markdown` header first
3. If server returns markdown → display directly
4. If HTML → Turndown converts to clean markdown:
   - Strips scripts, styles, navigation, footers
   - Extracts main content from `<article>`/`<main>` tags
   - Converts headings, links, lists, code blocks, etc.
5. Toggle between "Markdown" (raw) or "Preview" (rendered) view

### Installation & Development

**Prerequisites:**
- [Bun](https://bun.sh/) runtime
- macOS (for native app development)

**Setup:**
```bash
bun install          # Install dependencies
bun run start        # Run in development mode
bun run build        # Build for current platform
bun run build:stable:win  # Build Windows x64
```

### Architecture
- **Bun Process** (`src/bun/index.ts`) — Handles HTTP requests, markdown conversion, tab state, RPC
- **Toolbar View** (Svelte compiled to JS) — Tab bar, navigation, URL input, markdown/preview toggle, content display

### Developer
[needle-tools](https://github.com/needle-tools)

### Related Tools
- Turndown (HTML to Markdown converter): https://github.com/turndown/turndown
- Electrobun: https://github.com/needle-tools/electrobun
