---
title: Microsoft BitNet - 1-bit LLM Inference Framework
anchor: Efficient CPU inference for 1.58-bit quantized LLMs with massive speedup
tags: [ai, llm, quantization, 1-bit, microsoft, inference, edge-ai]
description: Official Microsoft framework for running 1-bit LLMs efficiently on CPU/GPU
source_url: https://github.com/microsoft/BitNet
---

## My Reference

### Summary
BitNet is Microsoft's official inference framework for 1-bit LLMs (specifically BitNet b1.58). It enables efficient, lossless inference on CPU and GPU with massive performance gains and energy savings.

### Key Performance Metrics

| Platform | Speedup | Energy Reduction |
|----------|---------|------------------|
| **ARM CPUs** | 1.37x - 5.07x | 55.4% - 70.0% |
| **x86 CPUs** | 2.37x - 6.17x | 71.9% - 82.2% |

**Standout capability:** Can run a 100B BitNet b1.58 model on a single CPU at 5-7 tokens/sec (human reading speed).

### Official Models

| Model | Parameters | CPU Support |
|-------|------------|-------------|
| BitNet-b1.58-2B-4T | 2.4B | ✅ x86, ARM |
| bitnet_b1_58-large | 0.7B | ✅ |
| bitnet_b1_58-3B | 3.3B | ✅ |
| Llama3-8B-1.58-100B-tokens | 8.0B | ✅ |
| Falcon3 Family | 1B-10B | ✅ |

### Architecture

- **Kernel types:** I2_S, TL1, TL2
- **Based on:** llama.cpp + T-MAC lookup table methodologies
- **Quantization:** Ternary weights (-1, 0, +1) = 1.58 bits per parameter
- **GPU support:** Available (NPU coming next)

### Quick Start

```bash
# Clone and setup
git clone --recursive https://github.com/microsoft/BitNet.git
cd BitNet
conda create -n bitnet-cpp python=3.9
conda activate bitnet-cpp
pip install -r requirements.txt

# Download and setup model
huggingface-cli download microsoft/BitNet-b1.58-2B-4T-gguf --local-dir models/BitNet-b1.58-2B-4T
python setup_env.py -md models/BitNet-b1.58-2B-4T -q i2_s

# Run inference
python run_inference.py -m models/BitNet-b1.58-2B-4T/ggml-model-i2_s.gguf -p "You are helpful" -cnv
```

### Demo & Resources

- **Live demo:** https://bitnet-demo.azurewebsites.net/
- **Hugging Face:** https://huggingface.co/microsoft/BitNet-b1.58-2B-4T
- **Technical report:** https://arxiv.org/abs/2410.16144

### Why 1-bit LLMs Matter

1. **Massive compression** - 10x smaller than FP16
2. **Energy efficient** - 70%+ reduction in compute energy
3. **Local deployment** - Run 100B models on consumer CPUs
4. **No accuracy loss** - Lossless inference at 1.58-bit quantization
