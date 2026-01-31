---
title: memU - Memory Framework for Proactive AI Agents
anchor: Memory system for 24/7 agents like Clawdbot/Moltbot - alternative approach with proactive memory
tags: [ai-agents, memory-system, open-source, clawdbot, proactive-ai]
description: Memory framework for 24/7 proactive agents with continuous learning, intent capture, and reduced LLM costs
source_url: https://github.com/NevaMind-AI/memU
---

## Summary

memU is a memory framework built specifically for long-running, always-online AI agents. It enables proactive behavior by continuously capturing user intent and understanding context without needing explicit commands.

### Key Features

- **24/7 Proactive Agent**: Always-on memory that never sleeps, never forgets
- **User Intention Capture**: Remembers goals, preferences, and context across sessions automatically
- **Cost Efficient**: Reduces token costs by caching insights and avoiding redundant LLM calls

### Architecture

Three-layer hierarchical memory:
1. **Resource Layer**: Direct access to original data, proactive monitoring for patterns
2. **Item Layer**: Targeted fact retrieval, real-time extraction from interactions
3. **Category Layer**: Summary-level overview, automatic context assembly for anticipation

### Comparison to Clawdbot

- memU positions itself as an alternative to OpenClaw/Moltbot/Clawdbot
- Built specifically for proactive memory (vs reactive queries)
- Has both cloud (memu.so) and self-hosted options
- Uses PostgreSQL with pgvector for persistent storage

### Interesting Concepts

- **Proactive Memory Lifecycle**: Main agent ↔ MemU bot sync loop with continuous memory injection and suggestions
- **Use Cases**: Information recommendation, email management, financial monitoring
- **Custom LLM Support**: OpenRouter, VoyageAI, custom providers

### Quick Links

- Cloud API: https://api.memu.so
- Docs: https://memu.pro/docs
- Self-hosted: `pip install -e .` with Python 3.13+
