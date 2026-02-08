---
title: "Textream — Live Teleprompter for macOS"
anchor: "Local macOS teleprompter with Dynamic Island overlay and real-time voice tracking"
tags: [macos, teleprompter, video, streaming, productivity, local]
description: "Free macOS teleprompter app with Dynamic Island overlay, voice tracking, and on-device speech recognition"
source_url: "https://blog.fka.dev/textream/"
---

## Reference

### Summary
Textream is a free, locally-running teleprompter app for macOS 14+ that displays your script in a Dynamic Island-style overlay at the top of your screen. It highlights words in real-time as you speak using on-device speech recognition.

**Key Features:**
- **Dynamic Island Overlay** — Subtle notch-shaped overlay only visible to you
- **Real-Time Voice Tracking** — Highlights words as you speak using macOS on-device speech recognition
- **Live Voice Waveform** — Visual feedback for mic activity
- **Pause & Resume** — Tap any word to jump to position
- **Completely Private** — No cloud, no data leaves your Mac, no accounts
- **Adjustable Overlay** — Resize width and height for any screen

**Target Users:**
- Streamers (sponsor segments, announcements)
- Interviewers (questions on screen, eye contact maintained)
- Presenters (keynotes, demos)
- Podcasters (show notes, ad reads)

### Download & Install
- **Direct:** https://github.com/f/textream/releases/latest
- **Homebrew:** `brew install f/textream/textream`
- **Requirements:** macOS 14 Sonoma+, Apple Silicon or Intel

### First Launch Fix
If macOS blocks the app:
```bash
xattr -cr /Applications/Textream.app
```

### Developer
[fka.dev](https://blog.fka.dev/) — GitHub: https://github.com/f/textream
