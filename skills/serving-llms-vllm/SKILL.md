---
name: serving-llms-vllm
description: "Use when deploying an LLM for production serving — high-throughput inference with OpenAI-compatible API using vLLM."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [vllm, inference, serving, llm, quantization, openai-api]
    related_skills: [llama-cpp, huggingface-hub]
---

# vLLM — High-Throughput LLM Serving

## Overview

vLLM is a high-throughput, memory-efficient LLM serving engine with an OpenAI-compatible API. It uses PagedAttention to manage KV cache, achieving 2-4x higher throughput than naive implementations.

## When to Use

- Production serving of LLMs (7B to 405B parameters)
- OpenAI-compatible API for your own models
- Batch inference with high throughput requirements
- Multi-model serving with automatic request routing

Do NOT use for: local single-user inference (use llama.cpp or Ollama), model training or fine-tuning (use dedicated frameworks), or single-request latency-critical apps without batching.

## Installation

```bash
pip install vllm
# For specific hardware support
pip install vllm[cuda]     # NVIDIA GPUs
pip install vllm[rocm]     # AMD GPUs
```

## Quick Start

```bash
# Serve a model
python -m vllm.entrypoints.openai.api_server     --model meta-llama/Llama-3.1-8B-Instruct     --host 0.0.0.0     --port 8000

# With quantization for memory savings
python -m vllm.entrypoints.openai.api_server     --model meta-llama/Llama-3.1-8B-Instruct     --quantization awq     --dtype auto
```

## Usage with OpenAI Client

```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:8000/v1",
    api_key="token-abc123",  # vLLM doesn't validate by default
)

chat_completion = client.chat.completions.create(
    model="meta-llama/Llama-3.1-8B-Instruct",
    messages=[{"role": "user", "content": "Hello!"}],
)
```

## Common Pitfalls

1. **GPU memory** — vLLM caches the KV cache; ensure your GPU has enough VRAM (8B ~16GB, 70B ~80GB at FP16)
2. **Quantization** — AWQ or GPTQ can halve memory needs; use `--quantization awq`
3. **Tensor parallelism** — For multi-GPU, use `--tensor-parallel-size 2` etc.
4. **Max model length** — Set `--max-model-len` to avoid OOM on long sequences

## Verification Checklist

- [ ] Server starts without errors
- [ ] Model loaded and responds to completion requests
- [ ] OpenAI client can connect and stream responses
- [ ] Throughput meets requirements
