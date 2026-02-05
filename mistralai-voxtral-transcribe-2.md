---
title: MistralAI Voxtral Transcribe 2 - Audio to Text
anchor: When you need high-quality, low-latency speech-to-text transcription with speaker diarization
tags: [audio-transcription, mistralai, speech-to-text, ai, realtime-transcription]
description: MistralAI's Voxtral Transcribe 2 offers state-of-the-art transcription quality with speaker diarization and ultra-low latency
source_url: https://mistral.ai/news/voxtral-transcribe-2
---

## My Reference

### Summary
MistralAI released Voxtral Transcribe 2 — two next-generation speech-to-text models:
- **Voxtral Mini Transcribe V2** — batch transcription for files
- **Voxtral Realtime** — live transcription with sub-200ms latency

### Key Features

**Voxtral Mini Transcribe V2:**
- State-of-the-art accuracy (~4% WER on FLEURS)
- Speaker diarization (who said what)
- Context biasing (custom vocabulary/names)
- Word-level timestamps
- 13 languages supported
- Process up to 3-hour audio in single request
- $0.003/min — cheapest high-quality option
- Outperforms GPT-4o mini Transcribe, Gemini 2.5 Flash, Assembly Universal, Deepgram Nova

**Voxtral Realtime:**
- Sub-200ms latency configurable
- Novel streaming architecture (not chunked offline model)
- 4B parameters, runs on edge devices
- Apache 2.0 open weights
- Native multilingual (13 languages)
- Privacy-first for sensitive deployments

**Languages:** English, Chinese, Hindi, Spanish, Arabic, French, Portuguese, Russian, German, Japanese, Korean, Italian, Dutch

**Use Cases:**
- Meeting intelligence with speaker attribution
- Voice agents & virtual assistants
- Contact center automation
- Live multilingual subtitles
- Compliance & documentation (GDPR/HIPAA compliant)

**Try it:**
- [Mistral Studio Audio Playground](https://console.mistral.ai/build/audio/speech-to-text) — upload up to 10 files, test diarization & timestamps
- API: Voxtral Mini Transcribe V2 at $0.003/min, Realtime at $0.006/min
- [Hugging Face](https://huggingface.co/mistralai/Voxtral-Mini-4B-Realtime-2602) — open weights for Realtime
