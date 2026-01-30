---
title: Agentation - Annotate Webpages for AI Agents
anchor: Debug/develop webpages by annotating elements with structured feedback for AI coding agents
tags: [ai, development, debugging, annotation, ui, react, claude-code, cursor]
description: Dev tool for annotating webpage elements to give AI agents precise context on what to change and why
source_url: https://agentation.dev/
---

## My Reference

### Overview
**Agentation** (agent + annotation) is a dev tool that lets you annotate elements on your webpage and generate structured feedback for AI coding agents.

### Key Problem It Solves
Without Agentation: "Fix the blue button in the sidebar" → Agent guesses wrong
With Agentation: `.sidebar > .nav-actions > button.primary` → Agent finds exact component

### How It Works

1. Click the toolbar icon to activate
2. Hover over elements to see names highlighted
3. Click any element to add an annotation
4. Write your feedback
5. Copy formatted markdown
6. Paste into Claude Code, Cursor, Windsurf, etc.

### Output Format
The tool generates markdown including:
- Element selector/class names
- Element position/description
- Your annotation/feedback

### Features
- **Zero dependencies** — Just React
- **Agent-agnostic** — Works with any AI tool
- **Text selection** — For typos or content issues
- **Animation pause** — Freeze animations to annotate specific frames
- **Desktop only** — Currently works on desktop browsers

### Use Cases
- Pointing out UI bugs with precise selectors
- Requesting design changes with exact element references
- Reporting visual regressions
- Teaching agents about component structure

### Best Practices
- Be specific — "Button text unclear" > "fix this"
- One issue per annotation
- Include context — expected vs. actual
- Use text selection for content issues
- Pause animations before annotating

### Inspiration
Based on [Benji Taylor's post on annotating for AI agents](https://benji.org/annotating)

### Resources
- **Website:** https://agentation.dev/
- **GitHub:** (not specified on site)
