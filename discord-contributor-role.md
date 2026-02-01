---
title: Discord Contributor Role (GitHub Integration)
anchor: Assign Discord roles automatically based on GitHub contributions
tags: [discord, github, automation, cloudflare-worker, roles, contributions]
description: Cloudflare Worker that assigns Discord roles to GitHub contributors
source_url: https://github.com/shi-gg/discord-contributor-role
---

## Summary

A Cloudflare Worker that automatically assigns Discord roles to members who have contributed to a GitHub repository. Uses Discord OAuth2 and GitHub OAuth2 for verification.

## Features

- Discord OAuth2 integration
- GitHub OAuth2 integration
- Automatic role assignment for verified contributors
- SQLite (D1) database for storing connections

## Tech Stack

- **Runtime:** Cloudflare Workers
- **Runtime:** Bun
- **Database:** SQLite (D1)
- **Auth:** Discord OAuth2 + GitHub OAuth2

## Environment Setup

**Discord:**
- Create app at Discord Developer Portal
- Add OAuth2 redirect: `http://localhost:8787/login/discord`
- Generate bot token and invite bot to server

**GitHub:**
- Create OAuth app at GitHub Developer Settings
- Add callback URL: `http://localhost:8787/login/github`
- Create Personal Access Token (no scopes needed)

**Configuration:**
- `DISCORD_SERVER_ID` - Server ID (enable dev mode to copy)
- `DISCORD_ROLE_ID` - Role ID to assign
- `GITHUB_OWNER` - Repository owner
- `GITHUB_REPO` - Repository name

## Database Schema

```sql
CREATE TABLE users (
  discord_id VARCHAR(22) PRIMARY KEY UNIQUE,
  github_id INTEGER64 UNIQUE,
  created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);
```

## Commands

```bash
bun install                    # Install dependencies
bunx wrangler d1 execute prod-d1-npmx --file=schema.sql --local  # Init D1 DB
bun run dev                    # Local development
bun run deploy                 # Deploy to Cloudflare Workers
```

## Use Cases

- Open source projects rewarding contributors
- Community building by linking GitHub activity to Discord presence
- Verified contributor identification system
