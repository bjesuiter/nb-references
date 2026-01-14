---
title: PI Coding Agent by Mario Zechner
anchor: Minimalist Terminal-Based AI Coding Agent
tags: [ai-agent, coding, terminal, pi-agent, mario-zechner]
description: A minimal, terminal-based AI coding agent philosophy and implementation
source_url: https://mariozechner.at/posts/2025-11-30-pi-coding-agent/
---

## My Reference

### Summary
Mario Zechner introduces "pi" - a minimalist, terminal-based AI coding agent built with Claude, emphasizing simplicity over complex tooling. The agent runs in a tmux session with the model seeing terminal output directly, avoiding sophisticated context engineering in favor of raw terminal interaction.

### Key Concepts

**Design Philosophy:**
- Minimalism over complexity - pi just gives the model a tmux session
- Direct terminal output visibility for the model
- "You are the agent" approach - model executes commands, human observes
- Inspired by Terminus 2 and the belief that context engineering hype is largely unfounded

**Architecture:**
- Claude as the model (Opus 4.5)
- tmux for terminal session management
- No sophisticated tool abstractions or context management
- Model sees raw terminal output, not UI-wrapped responses

**Context Gathering:**
- Using sub-agents mid-session signals poor planning
- Better to gather context first, create artifacts for later use
- pi can spawn itself via bash if needed

**Performance:**
- Benchmarked on Terminal-Bench 2.0 against Codex, Cursor, Windsurf, and other harnesses
- Competitive results despite minimal tooling
- Hundreds of exchanges in single sessions without context compaction

**Why Minimalism Works:**
- Terminal provides natural structure through prompts and command output
- Context engineering posts may be overthinking the problem
- The terminal itself provides the necessary scaffolding

**Lessons for Other Harnesses:**
- Simplicity can outperform complexity
- Context engineering may be less important than assumed
- Raw terminal visibility can replace sophisticated tooling
