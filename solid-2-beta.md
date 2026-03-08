---
title: Solid 2.0 Beta Release
anchor: Quick access when needing info on SolidJS 2.0 new features and migration
tags: [solidjs, javascript-framework, reactive, frontend, v2, beta, release]
description: SolidJS 2.0 beta release - major rewrite with async-first computations, new Suspense, actions, and optimistic primitives
source_url: https://github.com/solidjs/solid/releases/tag/v2.0.0-beta.0
---

## Reference

### Summary
SolidJS 2.0 enters beta - a major rewrite with async as first-class citizen, new reactivity model, and significant breaking changes.

### The Big Ideas

1. **Async is first-class**: Computations can return Promises (or async iterables) and the graph knows how to suspend/resume work.

2. **`<Suspense>` is for initial readiness**: Show a fallback while a subtree can't produce UI yet — then keep the UI stable while background work happens.

3. **Pending UI is an expression, not a flag**: `isPending(() => expr)` tells you when "refreshing..." work is in flight without tearing down the UI.

4. **Mutations have a home**: `action(...)` + optimistic primitives (`createOptimistic`, `createOptimisticStore`) let you write "optimistic → await → refresh" as one coherent flow.

5. **Derived state is a primitive**: Function forms like `createSignal(fn)` and `createStore(fn)` make derived-but-writable patterns explicit and composable.

6. **More predictable scheduler**: Updates are microtask-batched, and reads don't update until the batch flushes (use `flush()` only when you truly need "settle now").

7. **Dev guardrails**: Dev warnings catch accidental "top-level reads" in components and writes in reactive scopes before they become async bugs.

8. **DOM model cleanup**: `use:` directives are replaced by ref directive factories (with array composition), and `classList` is folded into `class`.

### Breaking Changes

- **List rendering**: `<Index>` is replaced by `<For>`, and For children receive accessors (`item()` / `i()`)
- **Effects & lifecycle**: `createEffect` is split (compute → apply), and `onMount` is replaced by `onSettled`
- **Stores**: Setters are draft-first by default; `storePath(...)` exists as opt-in helper
- **DOM**: `use:` directives removed; use ref directive factories instead

### Migration
- Beta tester guide: [documentation/solid-2.0/MIGRATION.md](https://github.com/solidjs/solid/blob/next/documentation/solid-2.0/MIGRATION.md)
- Vite Plugin Solid available under `next` tag

### Source
- Release: https://github.com/solidjs/solid/releases/tag/v2.0.0-beta.0
- Author: Ryan Carniato (Solid creator)
