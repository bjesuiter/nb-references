---
title: Deciduous - AI Agent Remembers Every Decision
anchor: when I want AI to remember design decisions in my codebase
tags: ai, memory, git, decision-tracking, context, tools
description: Build a living decision graph from git history - recover context when sessions end
source_url: https://deciduous.dev/
---

## Summary

Deciduous is a tool that creates a **decision graph** for your codebase. It:

- **Builds retroactively from git history** — analyzes commits to trace narratives
- **Keeps it alive as you work** — continuous tracking of decisions
- **Recovers full context when sessions end** — no more lost context
- **Ask questions, attach evidence, share with team**

## Key Features

- `/decision-graph` — Analyze git history and build connected decision graphs
- Tracks **goals**, **actions**, **observations**, and **pivots**
- Grounded entirely in repo data — no speculation
- Works with Claude, Codex, or any AI assistant

## Install

```bash
cargo install deciduous
deciduous serve   # Explore graph
deciduous pulse   # See summary
```

## Use Cases

- Onboard to a new codebase instantly
- Recover context after long breaks
- Understand why certain decisions were made
- Track design pivots over time
