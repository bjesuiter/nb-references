---
title: Voxtral WebGPU - Browser-based Real-time Speech Transcription
anchor: Real-time speech transcription running entirely in-browser with WebGPU
tags: [ai, speech-recognition, webgpu, browser, mistral, voxtral, privacy, open-source]
description: Real-time speech transcription tool running 100% locally in browser via WebGPU
source_url: https://x.com/xenovacom/status/1918876473726177301
---

## Reference

### Summary
Voxtral WebGPU is a browser-based real-time speech transcription tool that runs entirely locally on WebGPU. It uses Voxtral-Mini-4B from Mistral AI, supports 13 languages, achieves <500ms latency, and is fully private with zero cost.

### Key Details
- **Model**: Voxtral-Mini-4B (streaming ASR from Mistral AI)
- **Technology**: WebGPU (local inference, no server)
- **Languages**: 13 supported
- **Latency**: <500ms
- **Privacy**: Fully local, no audio sent to servers
- **Cost**: Zero (runs locally)

### Features
- Real-time transcription
- Streaming support
- Custom causal audio encoder
- All audio processing on device

### Source
- Account: Xenova (@xenovacom)
- Platform: X/Twitter
- Demo: https://huggingface.co/spaces/Xenova/voxtral-webgpu

### Related
- From the creator of Transformers.js
- Uses Transformers.js for WebGPU inference
