---
title: Google Local AI Models for Translation
anchor: local google ai model for translations offline
tags: [google, local-ai, translation, gemini, llama, offline]
description: Local AI models from Google for offline translation tasks
---

## My Reference

### TranslateGemma by Google DeepMind

Google DeepMind announced **TranslateGemma** — open translation models for local/offline use:

| Model | Size | Use Case |
|-------|------|----------|
| TranslateGemma 4B | 4B parameters | Runs locally on a smartphone |
| TranslateGemma 12B | 12B parameters | Desktop/local deployment |
| TranslateGemma 27B | 27B parameters | Higher quality, more resources |

**Key Features:**
- **55 languages** supported
- **Open models** — run on your own hardware
- **Offline capable** — no internet required after download
- **Efficiency-focused** — designed to balance speed and quality

### Gemma Models (General)

Google's open model family, which TranslateGemma is based on:

- **Gemma 3** - Latest generation (available in various sizes)
- Run locally via Ollama, LM Studio, vLLM, etc.
- Can be fine-tuned for translation tasks

### Related Tools

- **libretranslate** - Open source translation API (self-hosted)
- **argospm** - Argosoft translation (open source)
- **Google Translate API** - Cloud-based (not local)

### References

- https://github.com/google/gemma
- https://ollama.com/search?q=gemma
- https://libretranslate.com
