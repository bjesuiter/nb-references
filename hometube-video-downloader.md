---
title: Hometube - Self-hosted Video Downloader for Media Servers
anchor: Open-source tool to download videos for Plex/Jellyfin/Emby
tags: [video-downloader, self-hosted, media-server, go, plex, jellyfin, emby]
description: Hometube is a self-hosted web app that downloads videos from websites and organizes them for your home media server
source_url: https://opensourceprojects.dev/post/847fbf95-0188-4012-865c-642df5d4e04f
---

## Hometube Reference

**What it is:** A self-hosted video downloader that prepares videos for home media servers (Plex, Jellyfin, Emby).

### Key Features

- **Self-hosted web UI** — paste URL, download to specified directory
- **Automatic organization** — files stored with proper titles
- **Developer-friendly Go binary** — single executable, easy to deploy
- **Docker-ready** — slots into home lab setups
- **No cloud dependencies** — all data stays on your network

### Getting Started

1. **Repo:** [github.com/EgalitarianMonkey/hometube](https://github.com/EgalitarianMonkey/hometube)
2. **Download:** Pre-built binaries for Linux, macOS, Windows
3. **Run:** Starts web server on port 8080 → `http://localhost:8080`
4. **Configure:** Set download directory, paste video URL

### Use Case

For developers/tinkerers who want:
- Clean alternative to scattered download scripts
- Local alternative to cloud download services
- Videos ready for media server scanning

### Why It's Cool

- Focused utility (one job, done well)
- Simple Docker setup
- No usage limits or subscription
