---
title: qwen3_tts_rs - Qwen3 TTS Rust Implementation
anchor: Rust-based TTS with voice cloning, cross-platform CLI tools for AI agents
tags: [rust, tts, speech, ai, voice, open-source]
description: A Rust implementation of Qwen3 Text-to-Speech model inference with CLI tools for TTS and voice cloning
source_url: https://github.com/second-state/qwen3_tts_rs
---

## Reference

### Summary
Rust implementation of Qwen3 TTS with two CLI tools:
- `tts` - Generate voice wav files from text + named voice characters
- `voice_clone` - Generate voice from text + reference audio file

Supports libtorch (cross-platform, optional CUDA) and MLX (Apple Silicon Metal GPU).

### Key Features
- Cross-platform CLI tools suitable for AI agents/bots
- Voice cloning from reference audio
- Loads model weights from safetensors
- Complete neural network forward pass in Rust

### Links
- Crates: https://crates.io/crates/qwen3_tts
- Related: qwen3_asr_rs (Speech-to-Text), qwen3_audio_api (OpenAI compatible API)
