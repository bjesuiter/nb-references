---
title: Ralph Loop Essentials (2026-01-16)
anchor: Key patterns for Ralph autonomous loop system
tags: [ralph, autonomous-loop, vibe-kanban, agent, pattern]
description: Core concepts and patterns for the Ralph autonomous loop system as of 2026-01-16
---

## Ralph Loop Essentials

### Core Pattern
Ralph is an autonomous agent loop system that:
1. Picks up tasks from a queue (typically from openloop notes)
2. Iterates through work items autonomously
3. Respects usage budgets and time limits
4. Reports progress back to the user

### Key Components

### 1. Task Selection
- Reads from openloop notes or kanban boards
- Prioritizes based on status tags (in_progress, ready, blocked)
- Selects one item at a time to avoid context overflow

### 2. Usage Budget Management
- Respects hourly/daily model limits
- Night mode: up to 98% of cycle budget
- Day mode: up to 75% of cycle budget
- Hard stop at 98% regardless of time

### 3. Loop Structure
```
While (within_budget AND within_time_limit):
  1. Check usage limits
  2. Select next task/item
  3. Execute work
  4. Update task status
  5. Log progress
  6. Report to user
```

### 4. Session Persistence
- Uses sub-agent sessions for long-running loops
- Supports continuation after usage reset
- Checkpoints progress to avoid duplication

### 5. Output
- Enhanced notes/files
- Refinement logs
- Morning summary for human review

### Related
- [[skill:vibe-kanban]] - Visual kanban project management
- [[skill:refine]] - Autonomous research loop
- nb openloops: - Task tracking notebook
