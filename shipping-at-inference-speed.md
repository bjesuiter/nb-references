---
title: Shipping at Inference-Speed by Peter Steinberger
anchor: The most influential article for JB's journey into agentic coding and clawdbot
tags: [agents, coding, workflow, steipete, codex, claude, openai, shipping, productivity, vibe-coding]
description: Peter Steinberger's transformative article on building software at inference speed using AI agents - the article that brought JB into clawdbot and coding with agents
source_url: https://steipete.me/posts/2025/shipping-at-inference-speed
---

## Summary

Peter Steinberger's landmark article published Dec 28, 2025 detailing his journey from traditional coding to "shipping at inference-speed" using AI agents. This piece fundamentally changed JB's approach to software development and introduced them to clawdbot.

## Key Concepts

### The Model Shift
- The unlock was GPT-5 and Codex - codex reads entire codebases before starting, leading to fewer retries
- Trust in the model grows with usage; eventually you stop reading most code and just watch it stream
- Language choice matters: TypeScript for web, Go for CLIs, Swift for macOS/iOS

### Codex vs Opus
- Codex takes 4x longer but often faster overall because you don't have to fix the fix
- Codex silently reads files for 10-15 minutes before writing - annoying but amazing results
- Plan mode becomes unnecessary with newer models; just start a conversation

### Oracle Pattern
- Built oracle 🧿 - a CLI that lets agents query GPT-5 Pro when stuck
- Instructions in global AGENTS.md; model sometimes triggers it autonomously
- Massive unlock, now less needed with GPT-5.2

### Workflow Insights
- Iterative development: build → play → refine → repeat
- Queue tasks; let codex chug along while you focus elsewhere
- Cross-reference projects: "look at ../project-folder and do the same here"
- Start with CLI, add UI later
- Trust level "trusted" for project folders lets the model read more

### The Mental Model Shift
> "Building software is like walking up a mountain. You don't go straight up, you circle around it... it's imperfect, but eventually you get to where you need to be."

### Infrastructure
- Multiple Macs via Jump Desktop for parallel work
- Tailscale for remote access
- Skills for automation (domains, DNS, frontends, etc.)
- docs:list script to force model to read documentation

## JB's Notes

This article brought JB into:
- clawdbot ecosystem
- Agentic coding workflows
- Thinking about AI as a collaborative partner

## Related

- [steipete/agent-scripts](https://github.com/steipete/agent-scripts) - AGENTS.MD and tooling
- [steipete/oracle](https://github.com/steipete/oracle) - The Oracle CLI
- [Clawdis](https://clawdis.ai/) - AI assistant with full system access
- [VibeTunnel](https://vibetunnel.sh/) - Terminal multiplexer project mentioned

## Quote

> "I burned a lot of tokens since then. Time for an update."
> — Opening line that resonated deeply with JB
