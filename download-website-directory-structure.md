---
title: Download Website Source Code with Directory Structure
anchor: Tools and methods for completely downloading a website while preserving directory structure
tags: [wget, httrack, website-download, web-scraping, mirror, offline-browsing]
description: Methods and tools for downloading a complete website including all assets and preserving the original directory structure
---

## Overview

Tools and techniques for downloading a website's complete source code while maintaining its directory structure for offline viewing, archiving, or analysis.

## Method 1: wget (Recommended)

The classic tool for recursive website downloads:

### Basic Mirror
```bash
wget --mirror \
  --convert-links \
  --adjust-extension \
  --page-requisites \
  --no-parent \
  https://example.com/
```

### Key Flags Explained
| Flag | Purpose |
|------|---------|
| `--mirror` | Recursive download (like -r -l inf -np) |
| `--convert-links` | Convert links to work offline |
| `--adjust-extension` | Add .html to files without extension |
| `--page-requisites` | Download CSS, images, JS |
| `--no-parent` | Don't ascend to parent directory |
| `-l 5` | Set recursion depth (default: 5) |
| `-np` | No parent (restrict to starting directory) |
| `-E` | Save HTML/CSS with proper extensions |
| `--restrict-file-names=unix` | Safe filenames for Unix |
| `-p` | Download page requisites |

### Complete Command
```bash
wget --mirror \
  --convert-links \
  --adjust-extension \
  --page-requisites \
  --no-parent \
  --limit-rate=100k \
  --wait=1 \
  https://example.com/
```

### Download Without External Resources
```bash
wget -r -np -k -E \
  --domains=example.com \
  https://example.com/
```

## Method 2: httrack (GUI Alternative)

Full-featured website copier with GUI:

### Installation
```bash
# macOS
brew install httrack

# Linux
sudo apt install httrack

# Windows
# Download from https://www.httrack.com/
```

### Command Line
```bash
httrack "https://example.com" \
  -O "/path/to/mirror" \
  "-*" \
  "+*.example.com/*" \
  "-*.png" \
  "-*.jpg"
```

### GUI (Recommended for Beginners)
```bash
webhttrack
```

## Method 3: curl (For Specific Files)

For downloading individual files while preserving structure:

```bash
# Download with path preservation
curl -O "https://example.com/path/to/file.js"

# Using wget for single files with structure
wget -x "https://example.com/path/to/file.js"
```

## Method 4: aria2c (Parallel Downloads)

For faster large site downloads:

```bash
aria2c -x 16 -s 16 \
  --dir=/path/to/mirror \
  --input-file=urls.txt
```

## Best Practices

### 1. Rate Limiting
```bash
wget --limit-rate=100k --wait=1 https://example.com/
```

### 2. Resume Interrupted Downloads
```bash
wget -c https://example.com/
```

### 3. Respect robots.txt
```bash
wget --adjust-extension --page-requisites -np -k -E -p https://example.com/
```

### 4. Handle Authentication
```bash
wget --user=username --password=password https://example.com/
```

## Use Cases

| Use Case | Recommended Tool |
|----------|-----------------|
| Static site mirror | wget |
| Full website archive | httrack |
| Specific assets only | curl + scripting |
| Large site (fast) | aria2c |

## Output Structure

After downloading, the structure will be preserved:
```
mirror/
├── index.html
├── about/
│   └── index.html
├── css/
│   └── style.css
└── js/
    └── app.js
```

## Related Tools

- **SiteSucker** (macOS) — GUI website downloader
- **Scrapy** — Python web scraping framework
- **PySpider** — Powerful web scraping system
- **WebCopy** (Windows) — Website copier

## Legal Considerations

⚠️ **Important:** Only download websites you have permission to access. Check:
- Terms of Service
- robots.txt
- Copyright and licensing

## JB's Notes

Go-to tool when:
- Downloading documentation for offline use
- Archiving project websites
- Analyzing website structure
- Creating offline mirrors

**Default choice:** `wget --mirror --convert-links --adjust-extension --page-requisites --no-parent`

For large sites, add `--limit-rate=100k` to avoid being blocked.
