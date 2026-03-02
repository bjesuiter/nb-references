---
title: pi-design-deck - Visual Design Deck for Pi Coding Agent
anchor: Present multi-slide visual decision decks with high-fidelity previews for architecture, UI, code diffs
tags: [pi, coding-agent, design, ui, architecture, visualization]
description: Tool for Pi coding agent that presents visual decision decks in browser with 2-4 high-fidelity previews per slide
source_url: https://github.com/nicobailon/pi-design-deck
---

## Reference

### Summary
Visual design deck tool for Pi coding agent that presents multi-slide decision decks in the browser. Each slide shows 2-4 high-fidelity previews (code diffs, architecture diagrams, UI mockups) for user selection.

### Usage
- Ask naturally: "show me 3 architecture options", "present UI directions for settings"
- Slash commands: `/deck`, `/deck-plan docs/plan.md`, `/deck-discover`
- Click "Generate another option" to add via SSE without page reload

### Install
```
pi install npm:pi-design-deck
```
Requires pi-agent v0.35.0+
