---
title: SuperTalk - Web Worker RPC Layer
author: Justin Fagnani
source_url: https://www.npmjs.com/package/supertalk
anchor: web worker rpc layer raw message passing abstraction
tags: [web-worker, rpc, javascript, typescript, messaging, justin-fagnani]
description: RPC layer for web workers to avoid raw message passing (beta)
---

## My Reference

**Supertalk** by Justin Fagnani — A lightweight RPC layer for Web Workers.

### Key Features

- **RPC abstraction** — Don't deal with raw `postMessage()` manually
- **Type-safe** — TypeScript support for worker communication
- **Simple API** - Call functions in workers like local functions
- **Beta** — Still experimental, use with caution

### Why Use It

Web Worker communication without Supertack:
```javascript
// Raw postMessage - verbose and error-prone
worker.postMessage({ type: 'compute', data: x });
worker.onmessage = (e) => { /* parse e.data */ };
```

With Supertalk:
```javascript
// RPC-style - clean and typesafe
const result = await workerProxy.compute(x);
```

### Notes

- Created by **Justin Fagnani** (known for Lit, web components)
- NPM: https://www.npmjs.com/package/supertalk
- Great for offloading heavy computation to workers
- Avoids serialization/deserialization headaches

### Alternatives

- **Comlink** - Similar RPC layer for workers (more mature)
- **Raw postMessage** - No abstraction (verbose but stable)
