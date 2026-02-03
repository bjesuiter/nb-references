---
title: Sanity - How We Solved the Agent Memory Problem
anchor: Distillation approach to agent memory - not summarization - keeps operational details instead of narrative
tags: [agent-memory, distillation, saniy, nuum, miriad, long-term-memory, context-management]
description: Sanity's solution to agent memory problems using distillation instead of summarization
source_url: https://www.sanity.io/blog/how-we-solved-the-agent-memory-problem
---

## Summary

The "goldfish problem": agents lose track of decisions, file paths, and context as conversation extends because summarization discards operational details while preserving narrative.

**Key insight:** It's not about context window size, it's about how you manage it.

## The Problem with Summarization

- After one summarization pass, useful details are gone
- After 3-4 passes, only narrative shape remains, not operational specifics
- Agents "know" authentication was discussed but can't continue work because actionable details are compressed away

## The Solution: Distillation, Not Summarization

Instead of summarizing unrelated material, distill by:
1. Finding sequences in context that are related
2. Extracting two "distillates":
   - **Narrative**: 1-2 sentences explaining what happened ("Debugged the redirect middleware")
   - **Facts**: List of established facts ("Build gets env vars from SAM scripts, not Vercel")

This way context gets clearer over time, not more clouded. Details are abstracted but not mushed together.

## Nuum Architecture (Sanity's Implementation)

- **Infinity pool context window**: Background process rewrites log regularly, keeping context at 40-60% saturation
- **Reflection mode**: Research agent with full access to message history = perfect recall
- **Three-tier memory:**
  - Tier 1: Temporal Memory (full fidelity, full-text searchable)
  - Tier 2: Distilled Memory (compressed history, 60% threshold trigger)
  - Tier 3: ???

**Results:** 7,400+ messages over 6 days, agent remains coherent, remembers file paths from early days, architectural decisions, accumulated context.

## Inspiration

- Letta's approach to core memories and background processing
- OpenCode's coding tools

## Try It

```bash
bunx @sanity-labs/nuum --repl
```

Currently supports Anthropic APIs only (PRs welcome). Open source.
