---
title: Monolith - Save Complete Web Pages as Single HTML File
anchor: CLI tool for bundling web pages into single HTML with embedded assets
tags: [monolith, rust, html, web-scraping, offline, single-file, cli, archive]
description: Monolith is a CLI tool and library for saving complete web pages as a single HTML5 file with embedded CSS, images, and JavaScript
source_url: https://github.com/Y2Z/monolith
crates_url: https://crates.io/crates/monolith
---

## Overview

**Monolith** ⬛️ — A data hoarder's dream: bundle any web page into a single HTML file.

Unlike "Save page as...", Monolith embeds CSS, images, and JavaScript as data URLs, producing a single HTML5 document that works offline.

**Stars:** 14.7k | **License:** CC0-1.0 (public domain)

## Installation

### Universal (Cargo)
```bash
cargo install monolith
```

### macOS
```bash
brew install monolith
# OR
sudo port install monolith
```

### Windows
```bash
choco install monolith
scoop install main/monolith
winget install --id=Y2Z.Monolith -e
```

### Linux
```bash
# Arch
pacman -S monolith

# Alpine
apk add monolith

# Void
xbps-install -S monolith

# Snap
snap install monolith

# Guix
guix install monolith

# Nix
nix-env -iA nixpkgs.monolith
```

### Pre-built Binaries
Download from: https://github.com/Y2Z/monolith/releases

## Quick Usage

### Basic Save
```bash
monolith https://example.com -o example.html
```

### From Pipe (stdin)
```bash
cat some-page.html | monolith -aIiFfcMv -b https://site.com - > page-with-assets.html
```

### With Custom Filename
```bash
monolith https://lyrics.github.io/db/P/Portishead/Dummy/Roads/ -o %title%.%timestamp%.html
```

## Options

| Flag | Description |
|------|-------------|
| `-a` | Exclude audio sources |
| `-b URL` | Use custom base URL |
| `-B domain` | Forbid assets from domain |
| `-c` | Exclude CSS |
| `-C file` | Read cookies from file |
| `-d domain` | Allow assets only from domain |
| `-e` | Ignore network errors |
| `-E encoding` | Save with custom encoding |
| `-f` | Omit frames |
| `-F` | Exclude web fonts |
| `-h` | Print help |
| `-i` | Remove images |
| `-I` | Isolate the document |
| `-j` | Exclude JavaScript |
| `-k` | Accept invalid TLS certificates |
| `-m` | Output in MHTML format |
| `-M` | Don't add timestamp/URL |
| `-n` | Extract NOSCRIPT contents |
| `-o file` | Output to file (`-` for stdout) |
| `-q` | Be quiet |
| `-t seconds` | Set timeout |
| `-u agent` | Custom User-Agent |
| `-v` | Exclude videos |
| `-V` | Print version |

## Domain Whitelisting/Blacklisting

### Whitelist Only (No External Assets)
```bash
monolith -I -d example.com -d www.example.com https://example.com -o example-only.html
```

### Blacklist Specific Domains
```bash
monolith -I -B -d .googleusercontent.com -d googleanalytics.com \
  https://example.com -o example-no-ads.html
```

## Dynamic Content

Monolith has no JS engine. For dynamic pages, pre-process with Chromium:

```bash
chromium --headless --window-size=1920,1080 \
  --run-all-compositor-stages-before-draw \
  --virtual-time-budget=9000 --incognito --dump-dom \
  https://github.com | monolith - -I -b https://github.com -o github.html
```

## Authentication

```bash
monolith https://username:password@example.com -o example.html
```

## Proxies

```bash
export https_proxy=http://proxy:8080
export http_proxy=http://proxy:8080
export no_proxy=localhost,127.0.0.1
monolith https://example.com
```

## Comparison

| Feature | Monolith | wget | Browser "Save As" |
|---------|----------|------|-------------------|
| Single file | ✅ Yes | ❌ No | ❌ No |
| Embedded assets | ✅ Data URLs | ❌ External refs | ⚠️ Sometimes |
| Works offline | ✅ Yes | ⚠️ Needs assets | ⚠️ Depends |
| JavaScript | ❌ No JS engine | ✅ Fetches | ✅ Renders |
| Authentication | ✅ Basic auth | ✅ Yes | ✅ Yes |

## Use Cases

1. **Archive articles** for offline reading
2. **Save documentation** before it disappears
3. **Preserve interactive demos** locally
4. **Data hoarding** — replace tabs with files
5. **Share pages** without broken links
6. **Web archiving** projects

## MHTML Format

```bash
monolith -m https://example.com -o page.mhtml
```

MHTML is a single-file archive format compatible with some browsers and archive tools.

## Cloud Usage (Apify Actor)

Run without installation via Apify:
```bash
echo '{"urls": ["https://news.ycombinator.com/"]}' | apify call -so snshn/monolith
```

## JB's Notes

**Go-to tool when:**
- Saving documentation for offline use
- Archiving articles before they vanish
- Creating single-file backups
- Replacing browser tabs with HTML files

**Tip:** Use `-I` (isolate) for cleaner, self-contained output

**Note:** Not for dynamic content — use Chromium pre-processing for SPA/rendering pages

## Related Tools

- **wget** — Recursive website downloads
- **httrack** — Full website mirrors
- **singlefile** — Browser extension alternative
- **WebArchive** — macOS-specific

## Links

- GitHub: https://github.com/Y2Z/monolith
- Crates.io: https://crates.io/crates/monolith
- Releases: https://github.com/Y2Z/monolith/releases
