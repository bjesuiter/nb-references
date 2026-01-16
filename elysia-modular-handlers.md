---
title: Modular Handlers in Elysia - Type-Safe Patterns
anchor: Writing modularized, type-safe handlers in Elysia correctly
tags: [elysia, bun, typescript, handlers, modular, plugin, encapsulation]
description: Guide for writing modular handlers in Elysia with proper type safety, scope control, and plugin architecture
source_url: https://elysiajs.com/
---

## Overview

Elysia is a TypeScript web framework for Bun with end-to-end type safety and a plugin-based architecture. Handlers are **encapsulated** by default, meaning each Elysia instance keeps its hooks to itself unless explicitly scoped.

## Core Concept: Encapsulation

```typescript
import { Elysia } from 'elysia'

// This instance is self-contained
const profile = new Elysia()
    .onBeforeHandle(({ query: { name }, status }) => {
        if (!name) return status(401)
    })
    .get('/profile', () => 'Hi!')

// Routes in 'profile' are NOT available in 'app'
const app = new Elysia()
    .use(profile)  // Import the plugin
    .patch('/rename', () => 'Ok! XD')
    .listen(3000)
```

## Key Patterns for Modular Handlers

### 1. Basic Plugin (Standalone)

```typescript
import { Elysia, t } from 'elysia'

// Create a reusable plugin
const user = new Elysia()
    .get('/profile', 'User Profile')
    .get('/settings', 'User Settings')

// Apply it to main app
const app = new Elysia()
    .use(user)
    .get('/', 'Home')
    .listen(3000)
```

### 2. Plugin with Configuration

```typescript
import { Elysia } from 'elysia'

// Plugin factory with config
const user = ({ log = false }: { log?: boolean } = {}) =>
    new Elysia()
        .onBeforeHandle(({ request }) => {
            if (log) console.log(request)
        })
        .get('/profile', 'User Profile')
        .get('/settings', 'User Settings')

const app = new Elysia()
    .use(user({ log: true }))
    .listen(3000)
```

### 3. Using Scopes (Export Hooks to Parent)

By default, hooks are **local** (only affect the instance and descendants). Use `as: 'scoped'` or `as: 'global'` to export hooks.

| Scope | Affects |
|-------|---------|
| `local` (default) | Current instance + descendants only |
| `scoped` | Parent + current instance + descendants |
| `global` | All instances that use the plugin |

```typescript
import { Elysia } from 'elysia'

const auth = new Elysia()
    .onBeforeHandle(
        { as: 'scoped' },  // Export to parent!
        ({ cookie, status }) => {
            if (!cookie.token.value) return status(401)
        }
    )
    .get('/profile', () => 'Profile')

const app = new Elysia()
    .use(auth)
    // This route now has auth check from 'auth' plugin
    .patch('/update', ({ body }) => updateProfile(body))
    .listen(3000)
```

### 4. Guard with Scope

```typescript
import { Elysia, t } from 'elysia'

const ageCheck = new Elysia()
    .guard({
        as: 'scoped',  // Apply to parent
        query: t.Object({
            age: t.Number(),
            name: t.Optional(t.String())
        }),
        beforeHandle({ query: { age }, status }) {
            if (age < 18) return status(403)
        }
    })
    .get('/profile', () => 'Hi!')
    .get('/settings', () => 'Settings')

const app = new Elysia()
    .use(ageCheck)
    // Age check applies to /dashboard too
    .get('/dashboard', () => 'Dashboard')
    .listen(3000)
```

### 5. Modular File Structure

```
src/
├── main.ts           # Entry point
├── plugins/
│   ├── auth.ts       # Auth plugin
│   ├── user.ts       # User routes plugin
│   └── cors.ts       # CORS plugin
└── routes/
    ├── api.ts        # API routes
    └── web.ts        # Web routes
```

**src/plugins/auth.ts:**
```typescript
import { Elysia, t } from 'elysia'

export const auth = new Elysia()
    .use(cors)  // Import other plugins
    .guard({
        as: 'scoped',
        beforeHandle: ({ cookie, status }) => {
            if (!cookie.auth.value) return status(401)
        }
    })
```

**src/main.ts:**
```typescript
import { Elysia } from 'elysia'
import { auth } from './plugins/auth'
import { user } from './plugins/user'

const app = new Elysia()
    .use(auth)
    .use(user)
    .listen(3000)
```

## Validation with TypeBox

Elysia uses TypeBox for schema validation with full type inference:

```typescript
import { Elysia, t } from 'elysia'

const user = new Elysia()
    .post(
        '/user',
        ({ body }) => createUser(body),
        {
            body: t.Object({
                name: t.String(),
                email: t.String({ format: 'email' }),
                age: t.Optional(t.Number())
            }),
            response: {
                201: t.Object({
                    id: t.String(),
                    name: t.String()
                })
            }
        }
    )
```

## Type Safety Benefits

- **End-to-end types**: Full type inference from schema
- **Runtime validation**: TypeBox validates before handler runs
- **Error types**: Automatic error response typing
- **IDE support**: Autocomplete for request/response types

## Related Documentation

- **Encapsulation**: https://elysiajs.com/tutorial/getting-started/encapsulation.md
- **Plugin**: https://elysiajs.com/tutorial/getting-started/plugin.md
- **Guard/Validation**: https://elysiajs.com/tutorial/getting-started/guard.md
- **Lifecycle**: https://elysiajs.com/tutorial/getting-started/life-cycle.md
- **TypeBox**: https://elysiajs.com/patterns/typebox.md

## JB's Notes

Key takeaways for modular Elysia handlers:
1. **Default is isolated** — hooks don't leak to parents
2. **Use `as: 'scoped'`** to export hooks to parent instances
3. **Plugins are just Elysia instances** — compose with `.use()`
4. **TypeBox for validation** — end-to-end type safety
5. **Configurable plugins** — factory functions for dynamic config
