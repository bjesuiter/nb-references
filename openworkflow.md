---
title: OpenWorkflow - TypeScript Workflow Engine
anchor: Durable, resumable workflow framework for TypeScript without extra servers - simpler alternative to Temporal
tags: [typescript, workflow, temporal-alternative, durable-execution, serverless]
description: TypeScript framework for durable workflows that survive crashes/deploys without extra servers
source_url: https://github.com/openworkflowdev/openworkflow
---

## Summary

**OpenWorkflow** is a TypeScript framework for building durable, resumable workflows without extra servers (unlike Temporal which requires a separate server).

### Key Features
- **Durable** - Survives crashes and deploys
- **Resumable** - Pick up exactly where left off
- **Type-safe** - Full TypeScript support
- **Step memoization** - Never repeat completed work
- **Automatic retries** - Built-in exponential backoff
- **Long pauses** - Sleep for seconds or months
- **Scheduled runs** - Start at specific time
- **Parallel execution** - Run steps concurrently
- **No extra servers** - Uses your existing database
- **Dashboard included** - Monitor and debug workflows
- **Production ready** - PostgreSQL and SQLite support

### Quick Start
```bash
npx @openworkflow/cli init
# or
pnpx @openworkflow/cli init
# or
bunx @openworkflow/cli init
```

### vs Temporal
- OpenWorkflow runs **in-process** (no separate server)
- Simpler setup than Temporal
- Uses existing database (PostgreSQL/SQLite)
- Dashboard for monitoring included

### Resources
- [Docs](https://openworkflow.dev/docs)
- [Quick Start](https://openworkflow.dev/docs/quickstart)
- [Architecture](https://github.com/openworkflowdev/openworkflow/blob/main/ARCHITECTURE.md)
- [Examples](https://github.com/openworkflowdev/openworkflow/tree/main/examples)
- [NPM](https://www.npmjs.com/package/openworkflow)
