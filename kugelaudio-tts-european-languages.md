---
title: KugelAudio - Open-Source TTS for European Languages
anchor: European language TTS model outperforming ElevenLabs
tags: [tts, text-to-speech, european-languages, open-source, voice-cloning, ai-audio]
description: Open-source TTS for 24 European languages with AR + Diffusion architecture, outperforming ElevenLabs
source_url: https://github.com/Kugelaudio/kugelaudio-open
---

## Summary

**KugelAudio** is an open-source text-to-speech model specifically trained for **24 European languages**. Built on Microsoft's VibeVoice architecture with AR + Diffusion, it achieves state-of-the-art results—**outperforming ElevenLabs** in human preference benchmarks (78% win rate, Rank #1).

## Benchmark Results

| Rank | Model | Score | Win Rate |
|------|-------|-------|----------|
| 🥇 1 | KugelAudio | 26 | 78.0% |
| 🥈 2 | ElevenLabs Multi v2 | 25 | 62.2% |
| 🥉 3 | ElevenLabs v3 | 21 | 65.3% |

Based on 339 human evaluations using Bayesian skill-rating (OpenSkill).

## Supported Languages (24 European)

**High Quality:** English 🇺🇸, German 🇩🇪, French 🇫🇷, Spanish 🇪🇸
**Supported:** Italian 🇮🇹, Portuguese 🇵🇹, Dutch 🇳🇱, Polish 🇵🇱, Russian 🇷🇺, Ukrainian 🇺🇦, Czech 🇨🇿, Romanian 🇷🇴, Hungarian 🇭🇺, Swedish 🇸🇪, Danish 🇩🇰, Finnish 🇫🇮, Norwegian 🇳🇴, Greek 🇬🇷, Bulgarian 🇧🇬, Slovak 🇸🇰, Croatian 🇭🇷, Serbian 🇷🇸, Turkish 🇹🇷

## Architecture

- **Base:** Microsoft VibeVoice
- **Text Encoder:** Qwen2-based language model
- **TTS Backbone:** Transformer layers generate speech representations
- **Diffusion Head:** Predicts speech latents via denoising diffusion
- **Acoustic Decoder:** Converts latents to audio waveforms

## Key Features

- 🏆 **State-of-the-art quality** - Beats ElevenLabs in human testing
- 🎭 **Pre-encoded voices** - warm, clear, default
- 🎤 **Emotional range** - shouting, singing, whispering, angry, neutral
- 🔒 **Audio watermarking** - Facebook AudioSeal for detection
- 🌐 **24 European languages**
- 🎯 **AR + Diffusion architecture**

## Installation

```bash
# Clone and run with uv (auto-dependencies)
git clone https://github.com/Kugelaudio/kugelaudio-open.git
cd kugelaudio-open
uv run python start.py

# With web UI (opens http://127.0.0.1:7860)
uv run python start.py ui --share
```

**Prerequisites:** Python 3.10+, PyTorch 2.0+, CUDA (recommended)

## Quick Usage

### Command Line
```bash
# Generate speech
uv run python start.py generate "Hello world!" -o hello.wav

# With specific voice
uv run python start.py generate "Warm greeting" --voice warm -o warm.wav

# Verify watermark
uv run python start.py verify audio.wav
```

### Python API
```python
from kugelaudio_open import KugelAudioForConditionalGenerationInference
import torch

device = "cuda" if torch.cuda.is_available() else "cpu"
model = KugelAudioForConditionalGenerationInference.from_pretrained(
    "kugelaudio/kugelaudio-0-open",
    torch_dtype=torch.bfloat16,
).to(device)

processor = KugelAudioProcessor.from_pretrained("kugelaudio/kugelaudio-0-open")

# Generate with watermark
inputs = processor(text="Hello world!", voice="default", return_tensors="pt")
inputs = {k: v.to(device) for k, v in inputs.items()}

with torch.no_grad():
    outputs = model.generate(**inputs, cfg_scale=3.0)

processor.save_audio(outputs.speech_outputs[0], "output.wav")
```

## Model Specs

| Model | Parameters | Quality | RTF | VRAM |
|-------|------------|---------|-----|------|
| kugelaudio-0-open | 7B | Best | 1.00 | ~19GB |

RTF = Real-Time Factor (lower = faster)

## Hosted API

For zero-setup usage: https://kugelaudio.com
- Ultra-low latency (39ms end-to-end)
- Python SDK available

## Audio Samples

Available for German voices:
- Whispering (soft)
- Female Narrator (professional)
- Angry Voice
- Radio Announcer

## Training Details

- **Data:** ~200,000 hours from YODAS2 dataset
- **Hardware:** 8x NVIDIA H100 GPUs
- **Duration:** 5 days
- **Institution:** Hasso-Plattner-Institut

## Authors

- **Kajo Kratzenstein** (kajo@kugelaudio.com)
- **Carlos Menke**

## Related

- [Microsoft VibeVoice](https://github.com/microsoft/VibeVoice) - Base architecture
- [YODAS2 Dataset](https://huggingface.co/datasets/espnet/yodas) - Training data
- [Facebook AudioSeal](https://huggingface.co/facebook/audioseal) - Watermarking
