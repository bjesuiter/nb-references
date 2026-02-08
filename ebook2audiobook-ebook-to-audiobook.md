---
title: "ebook2audiobook — E-Book to Audiobook Converter"
anchor: "Full pipeline to convert e-books to audiobooks with voice cloning, 1158+ languages, and multiple TTS engines"
tags: [ebook, audiobook, tts, voice-cloning, conversion, python, xttsv2]
description: "Complete e-book to audiobook pipeline with voice cloning support, 1158+ languages, XTTSv2, and multiple TTS engines"
source_url: "https://github.com/DrewThomasson/ebook2audiobook"
---

## Reference

### Summary
A full-featured e-book to audiobook converter with:
- Voice cloning support
- 1158+ languages
- Multiple TTS engines: XTTSv2, Piper-TTS, VITS, Fairseq, Tacotron2, YourTTS
- Gradio web interface + headless CLI mode
- Chapter detection and metadata preservation

**Supported Input Formats:**
- .epub, .mobi, .azw3, .pdf, .txt, .fb2, .lrf, .html, .rtf, .doc, .docx, .chm, .pdb, .odt, .cbr, .cbz, .prc, .pml, .snb, .cbc, .rb, .tcr
- OCR support for image-based files

**Output Formats:**
- .m4b, .m4a, .mp3, .mp4, .flac, .wav, .ogg, .aac, .mov, .webm
- Mono or stereo

### Quick Start

**Launch GUI (Web Interface):**
```bash
git clone https://github.com/DrewThomasson/ebook2audiobook.git
cd ebook2audiobook

# Linux/MacOS
./ebook2audiobook.command

# Windows
ebook2audiobook.cmd

# Open http://localhost:7860
```

**Headless Mode:**
```bash
# Linux/MacOS
./ebook2audiobook.command --headless --ebook /path/to/book.epub --language eng

# Windows
ebook2audiobook.cmd --headless --ebook /path/to/book.epub --language eng
```

### Key Features
- **Voice Cloning** — Use your own voice file for narration
- **Multi-Language** — 1158+ languages ([full list](https://dl.fbaipublicfiles.com/mms/tts/all-tts-languages.html))
- **SML Tags** — Fine-grained control over pauses and voice switching:
  - `[break]` — 0.3-0.6s silence
  - `[pause]` — 1.0-1.6s silence
  - `[pause:N]` — N seconds fixed pause
  - `[voice:/path/to/voice.wav]...[/voice]` — Switch voice
- **Custom Models** — Use your own fine-tuned XTTSv2 models
- **Docker Support** — CPU, CUDA, ROCm, XPU, Jetson

### Hardware Requirements
- **RAM:** 2GB min, 8GB recommended
- **VRAM:** 1GB min, 4GB recommended
- **CPU:** Works on any modern CPU (slower)
- **GPU:** CUDA, ROCm, MPS (Apple Silicon), XPU, Jetson supported

### TTS Engines
| Engine | Quality | Speed | Voice Cloning |
|--------|---------|-------|---------------|
| XTTSv2 | Highest | Near real-time | ✅ |
| BARK | High | Slow | ✅ |
| VITS | Good | Fast | ❌ |
| YOURTTS | Good | Medium | ✅ |
| Tacotron2 | Good | Medium | ❌ |
| Fairseq | Basic | Fast | ❌ |

### Usage Examples

**Basic Conversion:**
```bash
./ebook2audiobook.command --headless --ebook book.epub --language eng
```

**With Voice Cloning:**
```bash
./ebook2audiobook.command --headless --ebook book.epub --language eng --voice myvoice.wav
```

**Custom XTTSv2 Model:**
```bash
./ebook2audiobook.command --headless --ebook book.epub --language eng --custom_model mymodel.zip
```

**Public Share Link:**
```bash
./ebook2audiobook.command --share
```

### Docker

**Build:**
```bash
# Linux/MacOS
./ebook2audiobook.command --script_mode build_docker

# Windows
ebook2audiobook.cmd --script_mode build_docker
```

**Run GUI:**
```bash
# CPU
docker run --rm -it -p 7860:7860 ebook2audiobook:cpu

# CUDA
docker run --gpus all --rm -it -p 7860:7860 ebook2audiobook:cu128
```

**Headless:**
```bash
docker run --rm -it -v "/my/ebooks:/app/ebooks" \
  -v "/my/output:/app/audiobooks" \
  -p 7860:7860 ebook2audiobook:cpu \
  --headless --ebook "/app/ebooks/book.epub" --language eng
```

### Fine-Tuned Models
- Collection: https://huggingface.co/drewThomasson/fineTunedTTSModels/tree/main
- Training: https://huggingface.co/spaces/drewThomasson/xtts-finetune-webui-gpu

### Important Notes
- Only works with non-DRM, legally acquired eBooks
- EPUB lacks standard structure — manually remove unwanted text before conversion
- CPU mode is slow; GPU recommended for near real-time
- Docker is recommended to avoid dependency issues

### Links
- Demo: https://huggingface.co/spaces/drewThomasson/ebook2audiobook
- Colab: https://colab.research.google.com/github/DrewThomasson/ebook2audiobook/blob/main/Notebooks/colab_ebook2audiobook.ipynb
- Discord: https://discord.gg/63Tv3F65k6

### Developer
[DrewThomasson](https://github.com/DrewThomasson) | Ko-fi: https://ko-fi.com/athomasson2
