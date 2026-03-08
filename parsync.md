---
title: Parsync - Parallel rsync over SSH
anchor: Quick access when needing faster file sync tool that doesn't require rsync on target
tags: [rsync, ssh, sync, file-transfer, parallel, rust, CLI]
description: Parallel rsync-like pull sync over SSH with resume - no rsync needed on target, faster transfers
source_url: https://github.com/AlpinDale/parsync
---

## Reference

### Summary
A high-throughput, resumable pull sync from SSH remotes with parallel file transfers and optional block-delta sync. Doesn't require rsync on the target!

### Features
- **Parallel transfers** - Multiple files simultaneously
- **Resumable** - Resume interrupted syncs
- **Block-delta sync** - Optional delta compression for similar files
- **No rsync needed on target** - Only SSH required
- **Cross-platform** - Linux, macOS, Windows support

### Installation
```bash
# Linux/macOS
curl -fsSL https://alpindale.net/install.sh | bash

# Windows
powershell -ExecutionPolicy Bypass -c "irm https://alpindale.net/install.ps1 | iex"

# Or via cargo
cargo install parsync
```

### Usage
```bash
# Basic sync
parsync -vrPlu user@example.com:/remote/path /local/destination

# With custom SSH port
parsync -vrPlu user@example.com:2222:/remote/path /local/destination

# Performance tuning
parsync -vrPlu --jobs 16 --chunk-size 16777216 --chunk-threshold 134217728 user@host:/src /dst
```

### Performance
- `--jobs` - Number of parallel jobs
- `--chunk-size` - Size of transfer chunks
- `--chunk-threshold` - Threshold for delta sync
- `--verify-existing` - Hash existing files before skip decisions
- `--sftp-read-concurrency` - Parallel per-file read requests

### Source
- GitHub: https://github.com/AlpinDale/parsync
- Platform support: Linux (x86, ARM), macOS, Windows
