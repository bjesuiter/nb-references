---
title: A Complete Guide to AGENTS.md
anchor: How to write clean, efficient AGENTS.md files for AI coding agents
tags: [agents-md, documentation, ai-agents, context-management, progressive-disclosure]
description: Complete guide to optimizing AGENTS.md files - avoid bloat, use progressive disclosure, maximize instruction budget
source_url: https://www.aihero.dev/a-complete-guide-to-agents-md
---

# AGENTS.md Optimization Guide

**Source:** https://www.aihero.dev/a-complete-guide-to-agents-md

---

## Why AGENTS.md Matters

AGENTS.md is a markdown file that customizes how AI coding agents behave in your repository. It sits at the top of the conversation history, below the system prompt.

**Two types of guidance:**
- **Personal scope:** Commit style, coding patterns
- **Project scope:** Project purpose, package manager, architecture decisions

> **Note:** Claude Code uses `CLAUDE.md` instead. Symlink them: `ln -s AGENTS.md CLAUDE.md`

---

## The Growth Problem

There's a natural feedback loop that causes AGENTS.md bloat:

```
Agent does something you don't like → You add a rule → Repeat hundreds of times → File becomes "ball of mud"
```

**Never auto-generate AGENTS.md files** — they prioritize comprehensiveness over restraint.

---

## The Instruction Budget

**Frontier LLMs can follow ~150-200 instructions consistently.**

Every token in AGENTS.md loads on **every request**, whether relevant or not:

| Scenario | Impact |
|----------|--------|
| Small, focused | More tokens for actual work |
| Large, bloated | Fewer tokens for work; agent confused |
| Irrelevant instructions | Token waste + distraction |

**Rule:** AGENTS.md should be as small as possible.

---

## The Staleness Problem

Documentation goes out of date quickly. For AI agents reading docs on every request, **stale information poisons context**.

**Dangerous:** Documenting file paths (they change constantly)
**Better:** Describe capabilities, overall shape, hints

---

## The Minimum Viable AGENTS.md

Be ruthless. Consider this the absolute minimum:

```markdown
# Project Description

This is a [one-sentence project description].

# Package Manager

This project uses [pnpm/bun/yarn].

# Build Commands

- Build: `pnpm build`
- TypeCheck: `pnpm typecheck`
```

That's honestly it. Everything else should go elsewhere.

---

## Progressive Disclosure

Instead of cramming everything in, use progressive disclosure:

```
AGENTS.md (minimal)
    └── docs/TYPESCRIPT.md (only loads when writing TS)
            └── docs/TESTING.md (nested reference)
                    └── specific test runner docs
```

### Move Language-Specific Rules to Separate Files

**Before (in AGENTS.md):**
```markdown
- Always use const instead of let
- Never use var
- Use interface instead of type
```

**After (in AGENTS.md):**
```markdown
For TypeScript conventions, see docs/TYPESCRIPT.md
```

**Benefits:**
- Rules only load when relevant
- Other tasks don't waste tokens
- File stays focused

---

## Nested AGENTS.md for Monorepos

You can place AGENTS.md in subdirectories — they merge with root level.

| Level | Content |
|-------|---------|
| **Root** | Monorepo purpose, package navigation, shared tools |
| **Package** | Package purpose, specific tech stack, package conventions |

**Example:**

`/` (root AGENTS.md):
```markdown
This is a monorepo containing web services and CLI tools.

Use pnpm workspaces to manage dependencies.

See each package's AGENTS.md for specific guidelines.
```

`packages/api/AGENTS.md`:
```markdown
This package is a Node.js GraphQL API using Prisma.

Follow docs/API_CONVENTIONS.md for API design patterns.
```

---

## What Goes Where

| Location | When to Use |
|----------|-------------|
| **Root AGENTS.md** | Relevant to every single task |
| **Separate file** | Relevant to one domain (TypeScript, testing) |
| **Nested docs tree** | Can be organized hierarchically |

---

## Refactoring Prompt

Copy-paste this into your coding agent:

```
I want you to refactor my AGENTS.md file to follow progressive disclosure principles.

1. Find contradictions: Identify conflicting instructions
2. Identify essentials: Extract only root-level content
3. Group the rest: Organize by category (TypeScript, testing, etc.)
4. Create file structure: Minimal root + separate files
5. Flag for deletion: Remove redundant/obvious instructions
```

---

## Key Takeaways

1. **Keep it small** — 150-200 instructions max
2. **Don't document paths** — they change; document capabilities
3. **Use progressive disclosure** — link to separate files
4. **Nest for monorepos** — package-level AGENTS.md files
5. **Symlink for compatibility** — AGENTS.md ↔ CLAUDE.md

---

## Related

- [Humanlayer: Writing a Good CLAUDE.md](https://www.humanlayer.dev/blog/writing-a-good-claude-md)
- [Claude Code Documentation](https://docs.claude.com/)
