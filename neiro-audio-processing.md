---
title: neiro - Pure TypeScript Audio Processing Library
anchor: When I need a pure TypeScript audio processing library for BGFWT or similar projects
tags: typescript, audio, processing, bgfwt, serverless, npm
description: Chainable, immutable audio processing library for TypeScript - loudness normalization, true peak limiting, silence trimming, fades, slicing
source_url: https://github.com/tigerabrodi/neiro
---

## My Reference

### Summary
Pure TypeScript audio processing library with chainable API. No WASM, no native binaries, no ffmpeg needed. Runs anywhere: Node.js, Vercel, Cloudflare Workers, serverless.

### Key Features
- **Loudness normalization** (ITU-R BS.1770-4)
- **True peak limiting** (4x oversampling)
- **Silence trimming**
- **Fades** (in/out)
- **Slicing & concatenation**
- **Speed adjustment**
- **Export to MP3, WAV, PCM**

### Quick Example
```typescript
const track = await AudioTrack.fromBuffer({ buffer });
const result = track
  .normalize({ target: -14 })
  .trimSilence()
  .fadeOut({ ms: 10 });
writeFileSync("output.mp3", result.toMp3());
```

### Why It Matters for BGFWT
- Pure TypeScript → easy to bundle, no native deps
- Serverless-ready → works in Vercel/Cloudflare Workers
- Clean chainable API → great DX
- Small runtime deps (lamejs, audio-decode only)

### Install
```bash
bun add @tigerabrodioss/neiro
# or
npm install @tigerabrodioss/neiro
```
