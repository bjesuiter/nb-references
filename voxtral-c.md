---
title: voxtral.c - Pure C Voxtral STT Implementation
anchor: Pure C speech-to-text implementation with zero dependencies
tags: [c, speech-to-text, mistral, voxtral, inference, mps, metal]
description: Zero-dependency C implementation of Mistral's Voxtral Realtime 4B speech-to-text model
source_url: https://github.com/antirez/voxtral.c
---

## Summary

Pure C inference implementation of Mistral AI's Voxtral Realtime 4B speech-to-text model. Zero external dependencies beyond C standard library. Features Metal GPU acceleration on Apple Silicon, streaming output, and memory-mapped weights.

## Key Features

- **Zero dependencies**: Pure C with MPS backend (fastest on Apple Silicon) or BLAS for Intel/Linux
- **Metal GPU acceleration**: Automatic on M1/M2/M3 Macs with fused GPU ops
- **Streaming output**: Tokens stream to stdout as generated
- **Streaming C API**: Feed audio incrementally, get tokens back progressively
- **Memory-mapped weights**: BF16 safetensors load near-instantly
- **Chunked encoder**: Bounded memory regardless of input length
- **Rolling KV cache**: Capped at 8192 positions for unlimited audio length

## Usage

```bash
# Build for Apple Silicon
make mps

# Download model (~8.9GB)
./download_model.sh

# Transcribe
./voxtral -d voxtral-model -i audio.wav

# Pipe via ffmpeg
ffmpeg -i audio.mp3 -f s16le -ar 16000 -ac 1 - 2>/dev/null | \
  ./voxtral -d voxtral-model --stdin
```

## Motivation

antirez created this to provide a self-contained reference implementation, since Mistral only provided vLLM integration. Includes a simple Python reference implementation too.
