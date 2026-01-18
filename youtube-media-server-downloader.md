---
title: YouTube Video Downloader for Media Servers
anchor: Tools to download YouTube videos and organize for Plex/Jellyfin/Emby
tags: [youtube, video-downloader, media-server, yt-dlp, plex, jellyfin]
description: Tools and workflows for downloading YouTube videos and preparing them for home media servers
---

## YouTube Downloader for Media Servers

### Recommended Tool: yt-dlp

**yt-dlp** is the industry-standard YouTube downloader with extensive features for media server preparation.

### Key Features

- **Format selection** — Download best quality video + audio
- **Metadata embedding** — Title, description, thumbnails embedded in file
- **Thumbnail extraction** — Download thumbnails as separate files
- **Series/playlist organization** — `--download-archive` to avoid duplicates
- **Custom templates** — Format filenames with series/season info
- **SponsorBlock** — Auto-remove sponsor segments

### Example Commands

```bash
# Basic download best quality
yt-dlp -f "bv+ba[ext=m4a]/best" -o "%(title)s.%(ext)s" "URL"

# For Plex/Jellyfin with metadata
yt-dlp --embed-thumbnail --write-description \
  -o "%(upload_date)s - %(title)s - %(id)s.%(ext)s" \
  "URL"

# Download playlist as series
yt-dlp --download-archive archive.txt \
  --write-info-json --write-thumbnail \
  -o "%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s" \
  "PLAYLIST_URL"

# Skip already downloaded
yt-dlp --download-archive downloaded.txt "URL"
```

### Filename Templates for Media Servers

```bash
# Plex compatible: "Season/Episode - Title.ext"
yt-dlp -o "%(series)s/%(season_number)sx%(episode_number)s - %(title)s.%(ext)s"

# With date: "YYYY-MM-DD - Title.ext"
yt-dlp -o "%(upload_date)s - %(title)s.%(ext)s"
```

### Dependencies (macOS)

```bash
brew install yt-dlp ffmpeg
# ffmpeg required for format merging and thumbnail embedding
```

### Alternatives

| Tool | Pros | Cons |
|------|------|------|
| yt-dlp | Most features, active dev | CLI only |
| Stacher | GUI for yt-dlp, presets | macOS only |
| TubeSync | Full GUI, PVR style | Heavy resource use |
| Hometube | Web UI, self-hosted | Less YouTube-focused |

### Related

- See [Hometube](hometube-video-downloader.md) for general web video downloading
