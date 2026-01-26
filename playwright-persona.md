---
title: Playwright Persona 🎭
anchor: Declarative authentication testing library for Playwright using personas
tags: [playwright, testing, authentication, e2e, typescript, javascript]
description: Library for testing authenticated websites in Playwright using a declarative persona-based approach
source_url: https://github.com/kettanaito/playwright-persona
---

## Overview

**Playwright Persona** is a library for testing authentication-dependent behaviors in Playwright using a declarative, persona-based approach.

## Why Playwright Persona?

### Problems with Official Recommendations

- **Imperative:** Requires separate auth project, manual session storage, and marking dependent tests
- **Global setup:** Shared state between tests leads to flakiness (test order issues)
- **Unopinionated:** No strong defaults for predictable experience

### Solution: Persona Strategy

| Feature | Description |
|---------|-------------|
| **Declarative** | `await authenticate({ as: 'user' })` |
| **Test case-based** | Isolated auth state per test (unique users, unique sessions) |
| **Performant** | Caches valid sessions on disk, reuses when valid |
| **Flexible** | Supports any auth strategy via custom recipes |

## Installation

```bash
npm i playwright-persona --save-dev
```

**Important:** Add `playwright/.auth` to `.gitignore` (contains sensitive session data)

## Usage

### 1. Define Personas

```typescript
// tests/personas.ts
import { definePersona } from 'playwright-persona'

export const user = definePersona('user', {
  async createSession({ page }) {
    // Describe authentication steps
    await page.goto('/login')
    await page.getByLabel(/Username/).fill('john.doe')
    await page.getByLabel(/Password/).fill('supersecret')
    await page.getByRole('button', { name: /Log in/ }).click()
    
    return { user: { id: 'abc-123', username: 'john.doe' } }
  },
  async verifySession({ page, session }) {
    await page.goto(`/users/${session.user.username}/notes`)
    await page.getByText(/My notes/).waitFor({ state: 'visible' })
  },
})
```

### 2. Create Authentication Fixture

```typescript
// tests/fixtures/authenticate.ts
import { test, combinePersonas } from 'playwright-persona'
import { user } from '../personas'

export const test = test.extend({
  authenticate: combinePersonas(user),
})
```

### 3. Use in Tests

```typescript
// tests/cart.spec.ts
import { test } from '../fixtures/authenticate'

test('add item to cart', async ({ page, authenticate }) => {
  await authenticate({ as: 'user' })
  await page.goto('/products')
  // ... test actions
})
```

## Key Concepts

### Persona Definition
- `name` - Persona identifier
- `createSession` - Steps to authenticate and return session object
- `verifySession` - Verify session is still valid

### Session Caching
- Successful sessions stored in `./playwright/.auth`
- Reused across test runs if still valid
- Avoids re-running full auth flow

### Test Isolation
- Each test gets unique user/session
- No shared state between tests
- Eliminates test order flakiness

## Recipes

Supports various authentication strategies:
- Cookie-based auth
- Token-based auth (localStorage/sessionStorage)
- HTTP API authentication
- OAuth flows

## Official Playwright Integration

There's an [open proposal](https://github.com/microsoft/playwright/issues/36540) to bring this API natively to Playwright. Consider upvoting if you find it useful!

## Related

- [Playwright Authentication Docs](https://playwright.dev/docs/auth)
- [Playwright Official Issue](https://github.com/microsoft/playwright/issues/36540)
