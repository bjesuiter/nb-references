---
title: "voxmlx - Realtime Transcription with Voxtral in MLX"
anchor: "MLX implementation of Voxtral Mini Realtime for local speech-to-text on Apple Silicon"
tags: [mlx, speech-to-text, apple-silicon, local-llm, python, realtime]
description: "Realtime speech-to-text implementation using Voxtral Mini Realtime model in MLX for Apple Silicon"
source_url: "https://github.com/awni/voxmlx"
---

## Reference

### Summary
voxmlx is a Python package providing realtime speech-to-text transcription using [Voxtral Mini Realtime](https://huggingface.co/mistralai/Voxtral-Mini-4B-Realtime-2602) model, running locally via MLX on Apple Silicon.

**Key Features:**
- **Realtime Transcription** — Stream audio from microphone or transcribe files
- **MLX Optimized** — Runs on Apple Silicon (M1/M2/M3/M4 chips) via MLX framework
- **Voxtral Model** — Uses Mistral's Voxtral-Mini-4B-Realtime-2602
- **Quantization Support** — Convert and run with 4-bit quantization to reduce memory
- **Python API** — Simple `transcribe()` function for programmatic use

### Install
```bash
pip install voxmlx
```

### Usage

**Stream from microphone:**
```bash
voxmlx
```

**Transcribe file:**
```bash
voxmlx --audio audio.flac
```

**Python API:**
```python
from voxmlx import transcribe
text = transcribe("audio.flac")
print(text)
```

### Model Conversion
Convert weights to MLX format with optional quantization:
```bash
# Basic conversion
voxmlx-convert --mlx-path voxtral-mlx

# 4-bit quantized
voxmlx-convert -q --mlx-path voxtral-mlx-4bit

# Convert and upload to HuggingFace
voxmlx-convert -q --mlx-path voxtral-mlx-4bit --upload-repo username/voxtral-mlx-4bit
```

### Requirements
- macOS with Apple Silicon
- MLX framework
- Python

### Developer
[awni](https://github.com/awni) — 7 stars on GitHub

### Related
- MLX: https://github.com/ml-explore/mlx
- Voxtral Model: https://huggingface.co/mistralai/Voxtral-Mini-4B-Realtime-2602
