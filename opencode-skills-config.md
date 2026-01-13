---
title: OpenCode Skills Configuration Documentation
anchor: when I need to configure agent skills in OpenCode
tags: opencode, skills, config, documentation
description: Official OpenCode docs for skills configuration and discovery
source_url: https://opencode.ai/docs/skills/
---

## My Reference

### Summary

Official documentation for OpenCode skills system. Skills are markdown files that OpenCode discovers and uses to configure agent behavior.

**Key locations for skills:**
- Project config: `.opencode/skill/<name>/SKILL.md`
- Global config: `~/.config/opencode/skill/<name>/SKILL.md`
- Claude-compatible: `.claude/skills/<name>/SKILL.md`

### Content

Skills must have YAML frontmatter with:
- `name` (required)
- `description` (required)

OpenCode walks up from current working directory to find skill definitions and loads global skills from the config directory.
