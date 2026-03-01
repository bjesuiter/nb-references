---
title: Harness Engineering - Leveraging Codex in an Agent-First World
anchor: OpenAI's experiment building software with 0 lines of human-written code
tags: [openai, codex, ai-agents, harness-engineering, software-development, agent-first]
description: OpenAI's 5-month experiment building a product with 100% agent-generated code (~1M lines, 1500 PRs, 1/10th the time)
source_url: https://openai.com/index/harness-engineering/
---

## Summary

OpenAI's engineering team built and shipped an internal product with **0 lines of manually-written code** over 5 months:
- ~1 million lines of code (app, infra, tooling, docs)
- 1,500 PRs merged
- 3.5 PRs per engineer per day (team grew to 7 engineers)
- ~1/10th the time vs human-written code
- Daily internal users + external alpha testers

**Core philosophy:** "Humans steer. Agents execute."

## Key Insights

### 1. The Role Shift: Engineer → Architect of Environments

> "The primary job of our engineering team became enabling the agents to do useful work."

Human engineers no longer write code. Instead they:
- Design environments and abstractions
- Specify intent clearly
- Build feedback loops for reliable agent work
- Identify missing capabilities when agents fail

### 2. Repository as System of Record

Instead of a monolithic AGENTS.md encyclopedia:
- **AGENTS.md** = table of contents (~100 lines)
- **docs/** = structured knowledge base
- **Plans** = first-class artifacts (execution plans with progress logs)

**Problems with giant instruction files:**
- Context crowds out task
- Everything important = nothing important
- Documentation rots instantly
- Hard to verify/validate

### 3. Agent Legibility > Human Preferences

Codebase is optimized for Codex to reason about it:
- Versioned, repo-local artifacts only
- Google Docs, Slack threads = inaccessible to agents
- "That Slack discussion? If it isn't discoverable to the agent, it's illegible."

**Technology choices favor:**
- "Boring" tech (stable APIs, composable)
- Reimplementing subsets vs opaque upstream behavior
- Full test coverage, OpenTelemetry integration

### 4. Architectural Constraints as Multipliers

Agents work best with **strict boundaries and predictable structure**.

**Architecture model:**
- Each domain = fixed layers (Types → Config → Repo → Service → Runtime → UI)
- Strict dependency directions enforced via custom linters
- Cross-cutting concerns enter through explicit "Providers" interface

**Enforced mechanically:**
- Custom linters (Codex-generated!)
- Structural tests
- Taste invariants (structured logging, naming conventions, file size limits)

> "This is the architecture you usually postpone until you have hundreds of engineers. With coding agents, it's an early prerequisite."

### 5. Throughput Changes Merge Philosophy

- Minimal blocking merge gates
- Short-lived PRs
- Test flakes = follow-up runs, not blockers
- "Corrections are cheap, waiting is expensive"

### 6. Increasing Autonomy Levels

Crossed threshold where Codex can now **end-to-end drive a feature**:

Given a prompt, Codex can:
1. Validate current state
2. Reproduce a bug
3. Record video of failure
4. Implement fix
5. Validate fix by driving the app
6. Record video of resolution
7. Open PR
8. Respond to feedback
9. Detect/fix build failures
10. Escalate only when judgment required
11. Merge the change

### 7. Entropy and Garbage Collection

**Problem:** Codex replicates existing patterns—even suboptimal ones.

**Solution:** "Golden principles" + recurring cleanup:
- Shared utilities over hand-rolled helpers
- Validate boundaries, don't probe "YOLO-style"
- Background Codex tasks scan for deviations
- Daily small refactors vs painful bursts

> "Technical debt is like a high-interest loan—pay it down continuously."

## Tools & Techniques

### Making Application Legible to Codex

- **Git worktrees** → boot isolated app instance per change
- **Chrome DevTools Protocol** → DOM snapshots, screenshots, navigation
- **Ephemeral observability stack** → logs, metrics, traces per worktree
- Codex queries logs with **LogQL**, metrics with **PromQL**

### The Ralph Wiggum Loop

Self-review cycle:
1. Codex reviews own changes locally
2. Request additional agent reviews (local + cloud)
3. Respond to feedback
4. Iterate until all agent reviewers satisfied

## Statistics

| Metric | Value |
|--------|-------|
| Duration | 5 months |
| Lines of code | ~1 million |
| PRs merged | 1,500 |
| Team size | 3 → 7 engineers |
| Throughput | 3.5 PRs/engineer/day |
| Time savings | ~90% (1/10th human time) |
| Agent runs | Up to 6+ hours (often overnight) |

## Key Quotes

> "We had weeks to ship what ended up being a million lines of code. To do that, we needed to understand what changes when a software engineering team's primary job is no longer to write code, but to design environments, specify intent, and build feedback loops."

> "When something failed, the fix was almost never 'try harder.' Because the only way to make progress was to get Codex to do the work, human engineers always stepped into the task and asked: 'what capability is missing, and how do we make it both legible and enforceable for the agent?'"

> "The resulting code does not always match human stylistic preferences, and that's okay. As long as the output is correct, maintainable, and legible to future agent runs, it meets the bar."

> "Building software still demands discipline, but the discipline shows up more in the scaffolding rather than the code."

## Related Concepts

- [Ralph Wiggum Loop](https://ghuntley.com/loop/) - Self-review cycle
- [Parse, Don't Validate](https://lexi-lambda.github.io/blog/2019/11/05/parse-don-t-validate/) - Boundary validation
- [Architecture.md](https://matklad.github.io/2021/02/06/ARCHITECTURE.md.html) - Top-level architecture map
- [Execution Plans](https://cookbook.openai.com/articles/codex_exec_plans) - First-class plan artifacts

## Links

- Original Article: https://openai.com/index/harness-engineering/
- Codex: https://openai.com/codex/
