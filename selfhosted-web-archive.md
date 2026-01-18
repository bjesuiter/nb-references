---
title: Self-hosted Internet Archive Solutions
anchor: Private, self-hosted tools to archive web pages like internet archive
tags: [self-hosted, archive, bookmarking, web-archive, wallabag, shiori]
description: Self-hosted solutions for saving and organizing web pages privately
---

## Self-hosted Web Archiving

### Recommended Tools

| Tool | Language |特点 | Docker |
|------|----------|------|--------|
| **Wallabag** | PHP | Full-featured, tags, export | ✅ |
| **Shiori** | Go | Simple, CLI + UI, bookmark manager | ✅ |
| **Monolith** | Rust | Single HTML file archive | ✅ |
| **Linkding** | Python/Django | Lightweight, modern UI | ✅ |
| **Wallabag v2** | PHP | Popular, feature-rich | ✅ |

### Wallabag

**Most full-featured self-hosted "read it later" app.**

```
# Docker setup
docker run -v /data/wallabag:/var/www/wallabag/data -p 80:80 wallabag/wallabag
```

- Save articles for later reading
- Full text extraction (removes ads/distractions)
- Tagging and organization
- Export to EPUB/PDF/MOBI
- Import from Pocket, Instapaper

### Shiori

**Simple bookmark manager with web UI and CLI.**

```bash
# Binary install
go install github.com/go-shiori/shiori@latest

# Docker
docker run -p 8080:8080 -v /data/shiori:/srv/shiori goshiori/shiori
```

- Minimalist interface
- Pocket import support
- CLI for scripting
- Archive pages as plain text/HTML

### Monolith

**Save web pages as single HTML files.**

```bash
# Install
cargo install monolith

# Usage
monolith "https://example.com" -o page.html
```

- No dependencies (single binary)
- Embeds CSS, images, fonts
- Works offline
- CLI-only

### Linkding

**Lightweight, modern bookmark manager.**

```bash
# Docker
docker run -p 8080:8080 -v /data/linkding:/data sissbruecker/linkding
```

- Simple tagging
- Fast search
- Bookmarks as favorites
- Browser extension

### Use Cases

| Need | Best Tool |
|------|-----------|
| Full "read it later" app | Wallabag |
| Simple bookmark manager | Linkding |
| CLI + scripting | Shiori |
| Offline HTML archives | Monolith |
| Pocket alternative | Wallabag or Shiori |

### Comparison

| Feature | Wallabag | Shiori | Monolith | Linkding |
|---------|----------|--------|----------|----------|
| Full text extraction | ✅ | ❌ | ❌ | ❌ |
| Tagging | ✅ | ✅ | ❌ | ✅ |
| CLI | ❌ | ✅ | ✅ | ❌ |
| Export | EPUB/PDF | HTML | HTML | Netscape |
| Pocket import | ✅ | ✅ | ❌ | ❌ |
| Resource usage | Medium | Low | Low | Low |

### Recommendation

- **Archive everything (full text)**: Wallabag
- **Bookmarks + CLI**: Shiori or Linkding
- **Single offline HTML files**: Monolith
