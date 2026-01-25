---
title: Pake - Package Websites as Desktop Apps
anchor: Turn any webpage into a desktop app without Electron
tags: [desktop-app, rust, tauri, packaging, electron-alternative]
description: CLI tool to package any website as a desktop app using Tauri - ~20x smaller than Electron
source_url: https://github.com/tw93/Pake
---

## My Reference

### Summary
Pake is a CLI tool to turn any webpage into a desktop app with one command. Built with Rust Tauri, ~5MB (20x smaller than Electron).

### Features
- **Lightweight:** ~5MB packages (20x smaller than Electron)
- **Fast:** Rust Tauri-based, low memory usage
- **Easy:** One-command packaging via CLI or online (GitHub Actions)
- **Rich:** Shortcuts, immersive windows, drag & drop, style customization, ad removal
- **Cross-platform:** macOS, Windows, Linux

### CLI Usage
```bash
# Install
pnpm install -g pake-cli

# Basic - auto fetches icon
pake https://github.com --name GitHub

# Advanced with custom options
pake https://weekly.tw93.fun --name Weekly \
  --icon https://cdn.example.com/icon.icns \
  --width 1200 --height 800 --hide-title-bar
```

### Ready-made Packages
- ChatGPT, Gemini, DeepSeek, Grok
- Twitter/X, YouTube, YouTube Music
- WeRead, LiZhi, Excalidraw, and more

### Alternatives to Electron
- Smaller footprint
- Faster startup
- Lower memory usage
