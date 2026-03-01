---
title: ATProto Starter - Minimal Bluesky/ATProto App with OAuth
anchor: Foundation for building ATProto apps with OAuth wired up, vanilla JS frontend
tags: [atproto, bluesky, oauth, starter, javascript, bun, elysia]
description: Minimal working foundation for building ATProto apps with OAuth out of the box
source_url: https://tangled.org/keithlaugh.love/atproto-starter
---

## Summary

A **minimal, working foundation** for building ATProto/Bluesky apps. OAuth works out of the box, sessions stored in SQLite, vanilla HTML/JS frontend (swap in any framework).

## Quick Start

```bash
git clone https://github.com/yourusername/atproto-starter
cd atproto-starter
cp .env.example .env
bun install
bun run dev
open http://127.0.0.1:3000
```

**Note:** Use `127.0.0.1`, not `localhost`. ATProto OAuth is picky about this.

## Project Structure

```
src/server/
├── index.ts           # Elysia server + routes
├── lib/
│   ├── oauth-client.ts    # OAuth configuration
│   ├── storage.ts        # Session/state stores (SQLite)
│   ├── db.ts             # Database setup
│   └── constants.ts      # App name, cookie config
├── middleware/
│   └── auth.ts           # requireAuth, optionalAuth
└── routes/
    └── oauth.ts          # login, callback, logout

src/types/
└── lexicons.ts          # Custom record types

public/
├── index.html           # Login page
├── styles.css           # Styles
└── app.js               # Client logic (vanilla JS)
```

## How ATProto OAuth Works

ATProto doesn't use centralized auth like "sign in with Google." Each user's data lives on their own PDS (Personal Data Server).

**Flow:**
1. User enters their handle (e.g., `keithlaugh.love`)
2. Your app figures out which PDS hosts their data
3. User is redirected to their PDS to authorize
4. PDS redirects back with an auth code
5. Your app exchanges code for tokens, stores session

### Local Development

ATProto has a "loopback client" system for local dev—skips registering anywhere, just works on `http://127.0.0.1:PORT`.

### Production

Serve OAuth client metadata at `/oauth-client-metadata.json`. Set `PUBLIC_URL` to your real domain.

## Using Authenticated Session

Routes can access user's DID and authenticated API client:

```typescript
import { requireAuth } from "./middleware/auth";

app
  .use(requireAuth)
  .get("/api/my-stuff", async ({ did, agent }) => {
    // did = user's DID (did:plc:abc123...)
    // agent = authenticated ATProto client
    
    const result = await agent.com.atproto.repo.listRecords({
      repo: did,
      collection: "com.example.settings",
    });
    
    return result.data.records;
  });
```

The `agent` is a fully authenticated [@atproto/api](https://github.com/bluesky-social/atproto/tree/main/packages/api) client.

## Custom Lexicons

Lexicons are ATProto's schema system—define what records your app stores in user repos.

### Lexicon ID Format

Reverse-DNS: `tld.domain.collection`

Examples:
- `com.myapp.settings` — user settings
- `com.myapp.post` — posts
- `com.myapp.graph.follow` — follow relationships

### Define Lexicons

```typescript
// src/types/lexicons.ts
export const LEXICON_IDS = {
  SETTINGS: "com.example.settings",
  POST: "com.example.post",
} as const;
```

OAuth scopes are built automatically from lexicon definitions.

### Store Records

```typescript
await agent.com.atproto.repo.createRecord({
  repo: did,
  collection: "com.example.post",
  record: {
    text: "hello world",
    createdAt: new Date().toISOString(),
  },
});
```

Records live in the user's PDS, not your server—they own their data.

### Read Records

```typescript
const result = await agent.com.atproto.repo.listRecords({
  repo: did,
  collection: "com.example.post",
  limit: 50,
});

for (const record of result.data.records) {
  console.log(record.value.text);
}
```

## Using Bluesky's Lexicons

Bluesky has built-in lexicons for common social features:

| Lexicon | Purpose |
|---------|---------|
| `app.bsky.feed.post` | Posts |
| `app.bsky.feed.like` | Likes |
| `app.bsky.feed.repost` | Reposts |
| `app.bsky.graph.follow` | Follows |
| `app.bsky.graph.block` | Blocks |
| `app.bsky.actor.profile` | Profile info |

### Request Scopes

In production, be specific:

```typescript
const OAUTH_SCOPES = [
  "atproto",
  "repo:app.bsky.feed.post",
  "repo:app.bsky.feed.like",
];
```

### Bluesky API Helpers

```typescript
// Post to Bluesky
await agent.post({
  text: "hello from my app",
});

// Get user's feed
const feed = await agent.getAuthorFeed({
  actor: did,
  limit: 20,
});

// Like a post
await agent.like(postUri, postCid);
```

## Frontend Options

Server serves static files from `/public/*` and exposes API routes. Swap in any framework:

### React
```bash
px create-vite . --template react-ts
# Build to public/ or proxy API calls
```

### Vue / Svelte / Whatever
Point at these API routes:
- `GET /api/me` — Check if logged in, get DID
- `GET /oauth/login?handle=user.bsky.social` — Start login
- `GET /oauth/logout` — Log out

### No Framework
Vanilla JS (~50 lines) works for simple apps.

## Environment Variables

```bash
# App URL (no trailing slash!)
PUBLIC_URL=http://127.0.0.1:3000

# Database (SQLite/Turso)
TURSO_DATABASE_URL=file:./data.db  # Local
# TURSO_DATABASE_URL=libsql://x.turso.io  # Production

# Optional
PORT=3000
NODE_ENV=development
```

## Production Checklist

- [ ] Set `PUBLIC_URL` to real domain
- [ ] Use Turso or hosted SQLite
- [ ] OAuth client metadata served at `/oauth-client-metadata.json`
- [ ] Set `NODE_ENV=production` for specific scopes
- [ ] Deploy on Bun or Node

## Community Tools

### Identity
- [Slingshot](https://slingshot.microcosm.blue/) — Fast DID/handle resolution cache
- [pdsls.dev](https://pdsls.dev) — Browse any ATProto repo

### Engagement
- [Constellation](https://constellation.microcosm.blue/) — Backlink index
- [Spacedust](https://spacedust.microcosm.blue/) — Real-time WebSocket for likes/reposts

## Tech Stack

- **Runtime:** Bun or Node.js
- **Server:** Elysia.js
- **Database:** SQLite (local) / Turso (production)
- **Auth:** ATProto OAuth
- **API:** @atproto/api
- **Frontend:** Vanilla JS (swap as needed)

## Links

- [ATProto Docs](https://atproto.com/docs)
- [Bluesky API Docs](https://docs.bsky.app/)
- [Lexicon Reference](https://atproto.com/specs/lexicon)
- [OAuth Spec](https://atproto.com/specs/oauth)
- [@atproto/api Package](https://github.com/bluesky-social/atproto/tree/main/packages/api)

## Related

- [Standard.site](/references/standard-site-atproto-publishing.md) — Publishing long-form content
- [WebTiles](/references/webtiles-atproto-modular-ui.md) — Composable UI widgets for ATProto
