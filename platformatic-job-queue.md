---
title: Platformatic Job Queue - Reliable Node.js Job Queue
anchor: Quick access when needing a reliable job queue library for Node.js from the Node maintainer
tags: [nodejs, job-queue, platformatic, background-jobs, library, mattteo-collina]
description: A reliable job queue for Node.js with deduplication, request/response support, and pluggable storage backends
source_url: https://github.com/platformatic/job-queue
---

## Reference

### Summary
A new job queue library for Node.js built by Matteo Collina (Node.js maintainer, Platformatic). Built for reliability from day one with deduplication, retries, request/response, and graceful shutdown.

### Features
- **Deduplication** - Prevents duplicate job processing with configurable result caching
- **Request/Response** - Enqueue jobs and wait for results with `enqueueAndWait()`
- **Multiple Storage Backends** - Redis/Valkey, filesystem, or in-memory
- **Automatic Retries** - Configurable retry attempts with exponential backoff
- **Stalled Job Recovery** - Reaper automatically recovers jobs from crashed workers
- **Graceful Shutdown** - Complete in-flight jobs before stopping
- **TypeScript Native** - Full type safety with generic payload and result types
- **Node.js 22.19+** - Uses native TypeScript type stripping

### Quick Start
```javascript
import { Queue, MemoryStorage } from '@platformatic/job-queue'

const storage = new MemoryStorage()
const queue = new Queue<{ email: string }, { sent: boolean }>({
 storage,
 concurrency: 5
})

queue.execute(async (job) => {
 console.log(`Processing job ${job.id}:`, job.payload)
 return { sent: true }
})

await queue.start()
await queue.enqueue('email-1', { email: 'user@example.com' })

// Or wait for result
const result = await queue.enqueueAndWait('email-2', { email: 'another@example.com' }, {
 timeout: 30000,
 resultTTL: 24 * 60 * 60 * 1000
})

await queue.stop()
```

### Why It Matters
Every Node.js developer has lost a background job to a server restart. This library solves that with built-in reliability features.

### Source
- GitHub: https://github.com/platformatic/job-queue
- npm: `npm install @platformatic/job-queue`
- Author: Matteo Collina (Node.js maintainer)
