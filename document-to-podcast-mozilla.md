---
title: Document to Podcast - Mozilla AI Blueprint
anchor: Convert documents to podcasts with two speakers using local AI models
tags: [podcast, ai, audio, document, mozilla, local-ai, tts, blueprint]
description: Mozilla AI blueprint for generating podcasts from documents using open-source local AI models
source_url: https://github.com/mozilla-ai/document-to-podcast
---

## Summary

**Document-to-Podcast** is a Mozilla.ai blueprint that converts documents into a podcast with two speakers using open-source, local AI models. No external APIs or GPU required.

## Key Features

- **Two-speaker podcast** — Generates natural dialogue between hosts
- **Fully local** — Runs on your machine, privacy-friendly
- **Open-source models** — Uses open-weight models (Qwen, etc.)
- **Works on most setups** — 8GB RAM, 20GB disk

## Quick Start

### CLI
```bash
pip install document-to-podcast

document-to-podcast \
  --input_file "document.pdf" \
  --output_folder "output/" \
  --text_to_text_model "Qwen/Qwen2.5-1.5B-Instruct-GGUF"
```

### GUI (Streamlit)
```bash
git clone https://github.com/mozilla-ai/document-to-podcast.git
cd document-to-podcast
pip install -e .
python -m streamlit run demo/app.py
```

### Cloud Options
- [Google Colab](https://colab.research.google.com/github/mozilla-ai/document-to-podcast/blob/main/demo/notebook.ipynb)
- [HuggingFace Spaces](https://huggingface.co/spaces/mozilla-ai/document-to-podcast)

## System Requirements

- **OS:** Windows, macOS, Linux
- **Python:** 3.10+ (3.12+ for Apple M chips)
- **RAM:** 8 GB minimum
- **Disk:** 20 GB minimum

## Example Use Cases

- Turn blog posts into podcast discussions
- Convert documentation into audio
- Create audio versions of articles
- Educational content in audio format

## Models Used

- **Text-to-text:** Qwen2.5-1.5B-Instruct (GGUF format)
- **TTS:** Open-source text-to-speech models

## Related

- Mozilla AI Blueprints: https://blog.mozilla.ai/introducing-blueprints-customizable-ai-workflows-for-developers/
- F5-TTS — Another local voice cloning option
- ElevenLabs — Cloud TTS alternative
