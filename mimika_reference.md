---
title: MimikaStudio - Local Voice Cloning & TTS for macOS
anchor: Local-first voice cloning app with MCP support for Apple Silicon
tags: [macos, voice-cloning, tts, mlx, apple-silicon, mcp, local-ai]
description: Voice cloning + TTS + PDF Read Aloud + Audiobook Creator for macOS
source_url: https://github.com/BoltzmannEntropy/MimikaStudio
---

## Summary

Local-first macOS application (Apple Silicon) with voice cloning, text-to-speech, document reader, and MCP agentic support. Runs fully on-device with Metal acceleration via MLX.

## Key Features

- **Voice Cloning**: Clone any voice from 3 seconds of reference audio (Qwen3-TTS, Chatterbox)
- **Text-to-Speech**: High-quality TTS (Kokoro, Supertonic, CosyVoice3)
- **PDF Read Aloud**: Document reader with sentence highlighting
- **Audiobook Creator**: Convert documents to audiobooks with queueable chapters
- **MCP Server**: Agentic voice cloning server with job queue orchestration

## Supported Models

| Model | Type | Languages |
|-------|------|-----------|
| Kokoro-82M | Fast TTS | English |
| Qwen3-TTS 0.6B/1.7B | Voice Cloning | 10 languages |
| Chatterbox | Voice Cloning | 23 languages |
| Supertonic-2 | TTS | 5 languages |
| CosyVoice3 | Expressive TTS | 10 languages |

## Tech Stack

- macOS (Apple Silicon only)
- MLX Native (Metal acceleration)
- Source-available (BSL-1.1)
