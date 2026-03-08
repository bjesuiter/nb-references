---
title: TanStack Intent - Ship Agent Skills with npm Packages
anchor: Quick access when needing to ship agent-readable skills alongside npm packages
tags: [tanstack, npm, agent-skills, cli, packaging, ai-agents, tooling]
description: CLI for library maintainers to generate, validate, and ship Agent Skills alongside npm packages - auto-discovered from node_modules
source_url: https://tanstack.com/blog/from-docs-to-agents
---

## Reference

### Summary
TanStack Intent is a CLI for library maintainers to generate, validate, and ship Agent Skills alongside their npm packages. Skills are versioned, auto-discovered from node_modules, and sync with npm updates.

### The Problem
- Docs target humans, not agents
- Types check API calls but can't encode intent
- Training data snapshots have version ambiguity
- Finding skills is manual, installing is manual, keeping current is manual
- Agents hallucinate, confuse versions at the frontier

### Solution
Skills travel with the tool via npm update — not training data, not community files. Versioned knowledge the maintainer owns.

### Features

**For Maintainers:**
- `px @tanstack/intent scaffold` - Generate skills from library
- `px @tanstack/intent validate` - Check skills are well-formed
- `px @tanstack/intent setup-github-actions` - CI workflow templates
- `px @tanstack/intent stale` - Check for version drift
- `px @tanstack/intent feedback` - Receive user reports when skills produce wrong output

**For Developers:**
- `px @tanstack/intent install` - Discover and wire skills into agent config
- `px @tanstack/intent list` - See available skills in deps
- Skills update automatically with npm update

### Skills Format
```yaml
---
name: tanstack-router-search-params
description: Type-safe search param patterns for TanStack Router
metadata:
  sources:
    - docs/framework/react/guide/search-params.md
---
## Search Params
Use `validateSearch` to define type-safe search params...
## Common Mistakes
❌ Don't access search params via `window.location`
```

### Adoption
Agent Skills spec already adopted by: VS Code, GitHub Copilot, OpenAI Codex, Cursor, Claude Code, Goose, Amp, and others.

### Source
- Website: https://tanstack.com/intent/latest
- Blog: https://tanstack.com/blog/from-docs-to-agents
- GitHub: https://github.com/TanStack/intent
- npm: `@tanstack/intent`
