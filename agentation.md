---
title: Agentation
anchor: Visual annotation tool for AI coding agents - lets you point at UI elements and generate structured feedback
tags: [ai, coding, tools, visual-feedback, annotation, dev-tools]
description: Dev tool to annotate webpage elements and generate structured feedback for AI coding agents
source_url: https://agentation.dev/
---

## Summary

Agentation (agent + annotation) is a dev tool that lets you annotate elements on your webpage and generate structured feedback for AI coding agents. Click elements, select text, add notes, and paste the output into Claude Code, Cursor, or any agent.

## How It Works

1. Click the icon in the bottom-right corner to activate
2. Hover over elements to see their names highlighted
3. Click any element to add an annotation
4. Write your feedback and click Add
5. Click to copy formatted markdown
6. Paste into your agent

## Key Insight

Agents can find and fix code much faster when they know exactly which element you're referring to. Agentation captures class names, selectors, and positions so the agent can locate the corresponding source files.

## Best Practices

- Be specific — "Button text unclear" is better than "fix this"
- One issue per annotation — easier for the agent to address individually
- Include context — mention what you expected vs. what you see
- Use text selection — for typos or content issues, select the exact text
- Pause animations — to annotate a specific animation frame

## Why It Matters

Without Agentation, you'd have to describe the element ("the blue button in the sidebar") and hope the agent guesses right. With Agentation, you give it `.sidebar > .nav-actions > button.primary` and it can grep for that directly.
