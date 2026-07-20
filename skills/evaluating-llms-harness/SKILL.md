---
name: evaluating-llms-harness
description: "Use when benchmarking LLMs with standardized evaluations — MMLU, GSM8K, HumanEval, and 100+ other tasks via lm-evaluation-harness."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [evaluation, benchmarking, lm-eval, nlp]
    related_skills: [huggingface-hub, llama-cpp, serving-llms-vllm]
---

# LM Evaluation Harness — LLM Benchmarking

## Overview

The `lm-evaluation-harness` (by EleutherAI) is the standard framework for evaluating LLMs across 100+ tasks: MMLU, GSM8K, HumanEval, HellaSwag, TruthfulQA, and more.

## When to Use

- Comparing model performance before deployment
- Testing a fine-tuned model against the base
- Writing evaluation reports for stakeholders
- Reproducing published benchmarks

## Installation

```bash
pip install lm-eval
# or from source
git clone https://github.com/EleutherAI/lm-evaluation-harness
cd lm-evaluation-harness
pip install -e .
```

## Basic Usage

```bash
# Evaluate a HuggingFace model on MMLU
lm_eval --model hf     --model_args pretrained=meta-llama/Llama-3.1-8B-Instruct     --tasks mmlu     --device cuda:0     --batch_size 4

# With a local vLLM server
lm_eval --model local-completion     --model_args model=meta-llama/Llama-3.1-8B-Instruct,base_url=http://localhost:8000/v1/completions     --tasks gsm8k

# Multiple tasks
lm_eval --model hf     --model_args pretrained=Qwen/Qwen2.5-7B-Instruct     --tasks mmlu,gsm8k,hellaswag,truthfulqa     --output_path ./results
```

## Results Format

Output is JSON with per-task accuracy, stderr, and config:

```json
{
  "results": {
    "mmlu": {
      "acc,none": 0.723,
      "acc_stderr,none": 0.008
    },
    "gsm8k": {
      "exact_match,flexible-extract": 0.582,
      "exact_match_stderr,flexible-extract": 0.017
    }
  }
}
```

## Common Pitfalls

1. **Task selection** — Not all tasks are relevant; pick tasks matching your use case
2. **Few-shot variance** — Different few-shot prompts yield different scores
3. **Tokenization** — Chat vs base models need different chat template handling
4. **GPU memory** — Larger models need `--model_args dtype=bfloat16` or quantization
5. **Reproducibility** — Always log the exact eval command and seed

## Verification Checklist

- [ ] At least one task runs to completion without errors
- [ ] Output path contains results JSON
- [ ] Results are reasonable (not all zeros or random)
- [ ] Model is correctly identified in the output
