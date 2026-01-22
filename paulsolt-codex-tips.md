---
title: Paul Solt's 7 Beginner Tips for Codex
anchor: Essential tips for getting started with Codex from Paul Solt (creator of Xcode MCP)
tags: [codex, ai-agent, paulsolt, getting-started, tips, workflow, xcode, swiftui, agent-skills]
description: Paul Solt's 7 beginner tips for getting started with Codex, plus his complete workflow video and agent super powers guide
source_url: https://x.com/PaulSolt/status/2014030873708945520
source_url_alt: https://youtu.be/o4iKnSYlhBQ
---

## Summary

Paul Solt (creator of Xcode MCP) shares 7 beginner tips for getting started with Codex. These are battle-tested recommendations from someone who has shipped seven apps using AI agents.

## Paul Solt's 7 Beginner Tips

### 1. Start with GPT-5.2-Codex high
> "That is high reasoning. It is enough. Don't be tempted with xhigh unless working on something really tricky. It uses more tokens and will be slower to finish."

**Recommendation:** Use `gpt-5.2-codex-high` for most tasks. Only use `xhigh` for complex problems.

### 2. Sometimes More Reasoning
*(Tip truncated in source — generally about adjusting reasoning levels per task)*

### 3. Use Project Structure
> "For new projects I have them copy the structure. See my workflow video."

**Tip:** Copy an existing project structure to give Codex context on your conventions.

### 4. Watch the Workflow Video
> How I use Codex GPT 5.2 with Xcode (My Complete Workflow)
> - YouTube: https://youtu.be/o4iKnSYlhBQ

### 5. Ask It to Do Things
*(And use YOLO mode when ready)*

### 6. YOLO Mode (Danger Mode)
> "You're going to need YOLO (danger mode) to get anything done without constant nagging."

**What is YOLO mode?**
- Codex has a `--yolo` or dangerous mode flag
- Allows auto-approval of changes without asking
- Speeds up development significantly
- Use when you trust the agent's direction

### 7. Use Agent Skills
> "Use this to give your agent super powers in Codex"

Agent Skills are an open format for giving agents new capabilities and expertise.

## Complete Workflow Video

**Video:** "How I use Codex GPT 5.2 with Xcode (My Complete Workflow)"
- URL: https://youtu.be/o4iKnSYlhBQ
- Covers: Xcode integration, project setup, agent workflow

## Super Powers with Agent Skills

Paul points to **agent-scripts** for extending Codex:

> "Lots of battle tested words in that project. More concepts for you and your agent to unpack and leverage."

**Resources:**
- **steipete/agent-scripts:** https://github.com/steipete/agent-scripts
- **Agent Skills:** Open format for agent capabilities

## For Your Skills

This connects to your **agent-skills repo**:

```
agent-skills/
├── skills/
│   ├── xcode-mcp/          # Paul Solt's Xcode MCP
│   ├── swiftui-*/          # SwiftUI skills
│   └── ...
├── AGENTS.md               # Codex/OpenCode config
└── README.md
```

**Your agent-skills should follow the pattern:**
- Clear SKILL.md with usage
- Copyable project structure
- Battle-tested prompts

## Key Takeaways for JB

| Tip | Action |
|-----|--------|
| 1. Use GPT-5.2-Codex high | Default model for most tasks |
| 2. Adjust reasoning | Match to task complexity |
| 3. Copy structure | Use your agent-skills templates |
| 4. Watch the video | Learn Paul's complete workflow |
| 5. Ask to do things | Be specific about outcomes |
| 6. Use YOLO mode | Enable for faster iteration |
| 7. Use Agent Skills | Extend capabilities |

## Related References

- `nb references:xcode-mcp.md` — Paul Solt's Xcode MCP for Codex
- `nb references:steipete-agent-scripts-codex.md` — Agent scripts for Codex
- `nb references:docsetquery-apple-docs.md` — SwiftUI docs for Codex
- `nb ideas:agent-skills/` — Your personal skill collection

## Paul's Background

- Created **Xcode MCP** — Model Context Protocol for Xcode
- Shipped **seven apps** using AI agents
- Works at Apple (previously GoPro)
- Shares weekly tips on YouTube and X

## Getting Started Checklist

- [ ] Install Codex CLI
- [ ] Configure `gpt-5.2-codex-high` as default
- [ ] Copy your agent-skills templates
- [ ] Watch Paul's workflow video
- [ ] Try YOLO mode on a small task
- [ ] Explore Agent Skills for extensions

## Links

- **Paul Solt on X:** https://x.com/PaulSolt
- **YouTube Channel:** https://www.youtube.com/user/PaulSolt
- **Xcode MCP:** https://github.com/steipete/xcode-mcp (fork) / Paul Solt's original
- **Agent Scripts:** https://github.com/steipete/agent-scripts
- **Your agent-skills:** https://github.com/bjesuiter/agent-skills
