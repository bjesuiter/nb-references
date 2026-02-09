---
title: Skyboard - ATProtocol Kanban Board
anchor: Trello-like kanban boards built on ATProtocol with Bluesky integration
tags: [atproto, bsky, kanban, board, trello, bluesky, social]
description: Skyboard is a Trello-like kanban board application built on ATProtocol with Bluesky integration
source_url: https://skyboard.dev/
---

## My Reference

### Summary
Skyboard is a Trello-like kanban board application built on the ATProtocol (atproto), the decentralized social protocol behind Bluesky. It allows users to create and manage kanban-style boards using their Bluesky/ATProtocol identity.

### Key Features
- Kanban board interface (Trello-like)
- Built on ATProtocol (decentralized social protocol)
- Bluesky authentication/integration
- Decentralized data ownership via atproto repos

### Technical Stack
- **Protocol:** ATProtocol (atproto)
- **Auth:** Bluesky accounts
- **Data:** Stored in user repositories on atproto PDS

### Related Projects
- Bluesky (app.bsky) - microblogging on atproto
- ATProtocol ecosystem

### Why Interesting
- First-class decentralized kanban boards
- User owns their data via atproto
- Can potentially interact with other atproto apps
- Alternative to centralized project management tools

### URL Structure
The share URL contains encoded state for board access:
- `iss` - issuer (PDS endpoint, e.g., bsky.social)
- `code` - board access code
