---
title: "Qwen3-TTS - Voice Cloning & Voice Design (macOS MLX)"
anchor: "Open-source TTS from Alibaba with 3-second voice cloning - fast on Apple Silicon via MLX"
tags: [tts, voice-cloning, qwen, alibaba, speech-synthesis, ai-audio, open-source, macos, apple-silicon, mlx]
description: "Alibaba's Qwen3-TTS enables 3-second voice cloning from audio clips, now with fast MLX inference on macOS"
source_url: "https://github.com/QwenLM/Qwen3-TTS"
---

## Reference

### Summary
Qwen3-TTS is an open-source text-to-speech model series by Alibaba's Qwen team, featuring:
- **Voice Cloning**: Clone any voice from just 3 seconds of reference audio
- **Voice Design**: Generate new voices from natural language descriptions
- **Custom Voice**: 9 premium pre-built voices across languages
- **Multi-language**: Supports 10 languages (Chinese, English, Japanese, Korean, German, French, Russian, Portuguese, Spanish, Italian)
- **Low latency**: 97ms end-to-end synthesis latency
- **Streaming**: Real-time streaming generation support

### macOS MLX Fast Inference
There's a dedicated Apple Silicon port for fast local inference on M1/M2/M3/M4 Macs:

**Repository**: https://github.com/kapi2800/qwen3-tts-apple-silicon

**Features**:
- Uses Apple's MLX framework for GPU inference
- Runs natively on Apple Neural Engine and GPU
- Better performance with less heat and battery drain
- 100% offline, no cloud API needed
- Supports voice cloning and custom voices

**Setup**:
```bash
git clone https://github.com/kapi2800/qwen3-tts-apple-silicon.git
cd qwen3-tts-apple-silicon
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
brew install ffmpeg
```

### Models Available
| Model | Size | Features |
|-------|------|----------|
| Qwen3-TTS-12Hz-1.7B-Base | 1.7B | Voice cloning, fine-tuning |
| Qwen3-TTS-12Hz-0.6B-Base | 0.6B | Voice cloning, fine-tuning |
| Qwen3-TTS-12Hz-1.7B-VoiceDesign | 1.7B | Voice design from text descriptions |
| Qwen3-TTS-12Hz-1.7B-CustomVoice | 1.7B | 9 premium voices with style control |
| Qwen3-TTS-12Hz-0.6B-CustomVoice | 0.6B | 9 premium voices |

### Quick Start
```bash
pip install qwen-tts

# Voice cloning with 3-second audio
from qwen_tts import Qwen3TTSModel
import torch

model = Qwen3TTSModel.from_pretrained(
    "Qwen/Qwen3-TTS-12Hz-1.7B-Base",
    device_map="cuda:0",
    dtype=torch.bfloat16,
)

wavs, sr = model.generate_voice_clone(
    text="Your text here",
    language="English",
    ref_audio="path/to/3sec-audio.wav",
    ref_text="Transcript of the reference audio",
)
```

### Resources
- **GitHub**: https://github.com/QwenLM/Qwen3-TTS
- **Hugging Face**: https://huggingface.co/collections/Qwen/qwen3-tts
- **Demo**: https://huggingface.co/spaces/Qwen/Qwen3-TTS
- **Blog**: https://qwen.ai/blog?id=qwen3tts-0115

### Why This Reference
- Open-source voice cloning (unlike ElevenLabs which is closed)
- 3-second cloning is extremely fast
- Self-hostable, no API costs
- Supports multiple languages and dialects
- Can design new voices from natural language descriptions

### Potential Use Cases
- Personal voice clones for TTS
- Character voices for games/apps
- Localization with original speaker's voice
- Accessibility tools
- Content creation with consistent voice branding
