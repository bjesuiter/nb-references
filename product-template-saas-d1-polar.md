---
title: "Product Template — SaaS Starter Kit with Cloudflare D1 + Polar Billing"
anchor: "Full-stack SaaS starter with authentication, billing, and dashboard using Cloudflare Workers + D1 + Polar"
tags: [saas, cloudflare, d1, polar, billing, hono, preact, drizzle, better-auth]
description: "Full-stack SaaS starter kit with authentication (BetterAuth), billing (Polar), and dashboard using Cloudflare Workers, D1, and Drizzle ORM"
source_url: "https://github.com/JoviDeCroock/product-template"
---

## Reference

### Summary
A production-ready SaaS starter template demonstrating how to integrate:
- **Cloudflare D1** (SQLite database via Drizzle ORM)
- **Polar** (billing, free/pro plans, webhooks)
- **BetterAuth** (authentication)
- **Hono** (Cloudflare Workers backend)
- **Preact + Vite** (frontend)

### Tech Stack
| Layer | Technology |
|-------|------------|
| Frontend | Preact, Vite, Tailwind CSS |
| Backend | Hono (Cloudflare Workers) |
| Database | Drizzle ORM + Cloudflare D1 (SQLite) |
| Auth | BetterAuth (email/password) |
| Billing | Polar (free/pro plans, webhooks) |

### Key Integrations

**Cloudflare D1 Setup:**
```bash
wrangler d1 create app-db
# Paste database_id into api/wrangler.jsonc
cd api && pnpm run db:migrate:remote
```

**Polar Billing Setup:**
1. Create Product in Polar (e.g., "Pro" plan)
2. Get Product ID → `POLAR_PRO_PRODUCT_ID`
3. Get Access Token → `POLAR_ACCESS_TOKEN`
4. Set up Webhook for events: subscription.updated, subscription.active, subscription.canceled, etc.
5. Get Webhook Secret → `POLAR_WEBHOOK_SECRET`

**Environment Variables:**

API (`api/.dev.vars`):
- `BETTER_AUTH_SECRET` — Session token signing key
- `BETTER_AUTH_URL` — API base URL
- `POLAR_ACCESS_TOKEN` — Polar API token
- `POLAR_WEBHOOK_SECRET` — Webhook signing secret
- `POLAR_PRO_PRODUCT_ID` — Pro plan product ID

Frontend (`web/.env`):
- `VITE_API_BASE_URL` — API URL

### Project Structure
```
├── web/           # Preact frontend (Vite)
│   └── src/
│       ├── components/
│       ├── pages/ # Home, Auth, Dashboard, Billing
│       └── models/ # Signal-based models
├── api/           # Hono backend (Cloudflare Workers)
│   └── src/
│       ├── db/    # Drizzle schema
│       ├── lib/   # Auth, plan logic
│       └── routes/ # API routes
```

### Quick Start
```bash
./setup.sh  # Copies env files, installs deps
cp api/.dev.vars.example api/.dev.vars
cp web/.env.example web.env

# Set up your API keys in the env files

cd api && pnpm run db:generate && pnpm run db:migrate:local

# Terminal 1
cd api && pnpm dev

# Terminal 2
cd web && pnpm dev
```

### Deployment

**API (Cloudflare Workers):**
```bash
cd api
wrangler login
wrangler d1 create app-db  # Update wrangler.jsonc with ID
pnpm run db:migrate:remote
wrangler secret put BETTER_AUTH_SECRET
wrangler secret put POLAR_ACCESS_TOKEN
wrangler secret put POLAR_WEBHOOK_SECRET
wrangler secret put POLAR_PRO_PRODUCT_ID
pnpm run deploy
```

**Frontend:**
```bash
cd web && pnpm build
# Deploy dist/ to Cloudflare Pages, Vercel, or Netlify
VITE_API_BASE_URL=https://api.yourdomain.com pnpm build
```

### Developer
[JoviDeCroock](https://github.com/JoviDeCroock)

### Resources
- Polar Docs: https://docs.polar.sh/
- Cloudflare D1: https://developers.cloudflare.com/d1/
- Hono: https://hono.dev/
