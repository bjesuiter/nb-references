---
title: "Electrobun — Bun-based Desktop App Framework"
anchor: "Build ultra-fast, tiny, cross-platform desktop apps with Bun, Zig, and Typescript"
tags: [bun, desktop, app, framework, typescript, zig, cross-platform]
description: "Complete solution for building, updating, and shipping ultra-fast, tiny, cross-platform desktop apps using Bun runtime and native Zig bindings"
source_url: "https://github.com/blackboardsh/electrobun"
website: "https://electrobun.dev"
---

## Reference

### Summary
Electrobun is a complete desktop app framework built with:
- **Bun** — Main process execution and webview bundling
- **Zig** — Native bindings
- **TypeScript** — Write both main process and webview code

**Key Benefits:**
- Small app bundles: ~12MB (uses system webview)
- Tiny updates: ~14KB (bsdiff patches)
- Fast, typed RPC between main and webview processes
- Everything integrated: code in 5 min, distribute in 10

### Quick Start
```bash
npx electrobun init          # Create new project
cd myapp
bun install                  # Install dependencies
bun dev                      # Run in development
bun run build               # Build for current platform
```

### Platform Support
| OS | Status |
|-----|--------|
| macOS 14+ | Official |
| Windows 11+ | Official |
| Ubuntu 22.04+ | Official |
| Other Linux (gtk3, webkit2gtk-4.1) | Community |

### Requirements

**macOS:**
- Xcode command line tools
- cmake (`brew install cmake`)

**Windows:**
- Visual Studio Build Tools with C++
- cmake

**Linux:**
- build-essential, cmake
- webkit2gtk, GTK development packages

```bash
# Ubuntu/Debian
sudo apt install build-essential cmake pkg-config libgtk-3-dev libwebkit2gtk-4.1-dev libayatana-appindicator3-dev librsvg2-dev
```

### Key Features
- **TypeScript Everywhere** — Main process and webviews without distinction
- **RPC Communication** — Fast, typed, easy isolation between processes
- **Self-Extracting Bundles** — ~12MB with system webview
- **Differential Updates** — ~14KB patches via bsdiff
- **Cross-Platform** — macOS, Windows, Linux

### Apps Built with Electrobun
- [Co(lab)](https://blackboard.sh/colab/) — Hybrid web browser + code editor for deep work

### Developer
[blackboardsh](https://github.com/blackboardsh) | Follow: [@BlackboardTech](https://twitter.com/BlackboardTech)

### Links
- Docs: https://blackboard.sh/electrobun/
- Discord: https://discord.gg/ueKE4tjaCE
