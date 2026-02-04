---
title: Schematron - Self-hosted LLM for HTML to JSON Extraction
anchor: Self-hosted specialized model for converting messy HTML to clean structured JSON
tags: [ai, html, json, extraction, scraping, open-source, self-hosted, schematron]
description: Schematron 8B/3B models for high-quality, low-cost HTML-to-JSON extraction with Pydantic/Zod support
source_url: https://inference.net/blog/schematron/
---

## My Reference

### Summary
Schematron is a family of specialized LLMs (8B and 3B variants) designed specifically for transforming messy HTML into clean, structured JSON. Delivers frontier-level extraction quality at 1-2% of the cost of general-purpose LLMs.

### Key Features
- **Two Models:** Schematron-8B (accurate) and Schematron-3B (fast)
- **128K token context** for long documents
- **Strict JSON mode** with 100% schema adherence
- **40-80x cheaper** than frontier models like GPT-5
- **10x faster** inference than general-purpose LLMs
- **Self-hosted** available via Hugging Face

### Usage Example (Python/Pydantic)
```python
from pydantic import BaseModel
from openai import OpenAI

class Product(BaseModel):
    name: str
    price: float
    specs: dict
    tags: list[str]

client = OpenAI(base_url="https://api.inference.net/v1", api_key=...)

response = client.chat.completions.parse(
    model="inference-net/schematron-8b",
    messages=[{"role": "user", "content": html}],
    response_format=Product,
)
```

### Self-Hosted Models
- Schematron-3B: https://huggingface.co/inference-net/Schematron-3B
- Schematron-8B: https://huggingface.co/inference-net/Schematron-8B

### Use Cases
- Web scraping at scale (1M+ pages/day)
- Product catalog aggregation
- Financial document parsing
- Web search grounding for LLMs
- Research data extraction

### Cost Comparison (100k pages)
Schematron models are 40-80x more affordable than frontier models for extraction tasks.
