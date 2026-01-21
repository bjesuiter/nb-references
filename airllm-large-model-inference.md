---
title: AirLLM - Run 70B Models on 4-8GB VRAM
anchor: Run large language models up to 70B on limited VRAM (4-8GB) without quantization
tags: [airllm, llm, inference, optimization, gpu, 70b, local-llm]
description: AirLLM optimizes inference memory usage, allowing 70B models to run on a single 4GB GPU without quantization, distillation, or pruning
source_url: https://github.com/lyogavin/airllm
---

## Summary

**AirLLM** enables running 70B+ large language models on consumer GPUs with only 4-8GB VRAM. No quantization, distillation, or pruning required.

## Key Capabilities

- **70B models on 4GB VRAM** — Llama3, Llama2, Mistral, etc.
- **405B models on 8GB VRAM** — Llama3.1 405B support
- **No quantization needed** — Run full precision models
- **Layer-wise loading** — Decomposes model during inference
- **3x speed boost** — Optional compression (4-bit/8-bit block-wise)

## Quick Start

```bash
# Install
pip install airllm

# Run 70B model
from airllm import AutoModel

model = AutoModel.from_pretrained("garage-bAInd/Platypus2-70B-instruct")

input_tokens = model.tokenizer(
    ["What is the capital of United States?"],
    return_tensors="pt",
    truncation=True,
    max_length=128,
    padding=False
)

output = model.generate(
    input_tokens['input_ids'].cuda(),
    max_new_tokens=20,
    use_cache=True
)

print(model.tokenizer.decode(output.sequences[0]))
```

## Supported Models

- **Llama3/3.1** — 70B on 4GB, 405B on 8GB
- **Llama2** — 70B on 4GB
- **Mistral** — 7B models
- **ChatGLM, QWen, Baichuan, InternLM** — Various sizes
- **Llama3.1 405B** — With 8GB VRAM + quantization

## Performance

| Model Size | VRAM Required | Notes |
|------------|---------------|-------|
| 70B | 4GB | Full precision |
| 405B | 8GB | With 4-bit/8-bit compression |

## macOS Support

- Works on Apple Silicon (M1/M2/M3)
- Requires: `mlx`, `torch`, Python native
- Example notebook: `run_on_macos.ipynb`

## Configuration Options

```python
from airllm import AutoModel

model = AutoModel.from_pretrained(
    "meta-llama/Llama-2-7b-hf",
    compression='4bit',      # 4bit or 8bit for 3x speed
    layer_shards_saving_path='/path/to/save',
    hf_token='HF_API_TOKEN', # For gated models
    prefetching=True,        # Overlap loading/compute
    delete_original=True     # Save disk space
)
```

## How It Works

1. **Layer decomposition** — Splits model layer-wise during first run
2. **On-demand loading** — Only loads layers needed for current inference
3. **Prefetching** — Overlaps loading with compute for speed
4. **Optional compression** — Block-wise quantization for 3x speed boost

## Requirements

- Python 3.x
- CUDA-capable GPU (4-8GB VRAM)
- Sufficient disk space for split model cache
- Optional: `bitsandbytes` for compression

## Troubleshooting

### Disk Space Error
- Safetensor deserialization errors → Clear disk space
- First run decompresses model → needs 2x disk temporarily

### Gated Models
- Pass `hf_token` for gated repos like Llama-2

## Links

- GitHub: https://github.com/lyogavin/airllm
- PyPI: https://pypi.org/project/airllm/
- Colab notebooks: https://github.com/lyogavin/airllm/tree/main/air_llm/examples
