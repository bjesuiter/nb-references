---
title: Playwright Chrome Extension for Agents
anchor: when I want to have an agent code a website, I could use this to connect it to a chrome extension - reduces context bloat of playwright mcp
tags: playwright, chrome-extension, agent, context, automation
description: Playwright integration via Chrome extension for AI agents - lighter than MCP
source_url: https://github.com/remorses/playwriter
---

## My Reference

### Summary

Playwright integration that connects AI agents to a Chrome extension instead of using Playwright MCP directly. Reduces context bloat by offloading browser automation to an extension.

**Benefits:**
- Less context overhead than full Playwright MCP
- Extension handles browser communication
- Agent sends high-level commands to extension
- Simpler, more focused interactions

### Content

Useful for:
- Agent-based web development
- Reducing token usage in browser automation
- Cleaner separation between agent logic and browser control
