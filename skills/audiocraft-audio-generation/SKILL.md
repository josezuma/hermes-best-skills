---
name: audiocraft-audio-generation
description: "Use when generating audio from text — MusicGen for music or AudioGen for sound effects using Meta's AudioCraft."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [audio, music-generation, audiocraft, musicgen, audio-gen]
    related_skills: [comfyui, heartmula]
---

# AudioCraft — Text-to-Audio Generation

## Overview

Meta's AudioCraft provides MusicGen (text-to-music) and AudioGen (text-to-sound-effects) models. Generate high-quality audio from natural language descriptions.

## When to Use

- Generating background music for videos
- Creating sound effects for games or demos
- Prototyping audio concepts from text descriptions
- Music production inspiration

## Installation

```bash
pip install audiocraft
# Or from source
git clone https://github.com/facebookresearch/audiocraft
cd audiocraft
pip install -e .
```

## MusicGen Usage

```python
from audiocraft.models import MusicGen
from audiocraft.data.audio import audio_write
import torch

# Load model
model = MusicGen.get_pretrained("facebook/musicgen-medium")  # or musicgen-small, musicgen-large
model.set_generation_params(duration=8)  # seconds

# Generate from text
descriptions = ["upbeat electronic dance music", "calm jazz piano"]
wav = model.generate(descriptions)  # 1 per description

# Save
for idx, one_wav in enumerate(wav):
    audio_write(f"output_{idx}", one_wav.cpu(), model.sample_rate, strategy="loudness", loudness_compressor=True)
```

## AudioGen Usage (sound effects)

```python
from audiocraft.models import AudioGen

model = AudioGen.get_pretrained("facebook/audiogen-medium")
model.set_generation_params(duration=5)

descriptions = ["dog barking", "rain on roof", "car engine starting"]
wav = model.generate(descriptions)

for idx, one_wav in enumerate(wav):
    audio_write(f"sfx_{idx}", one_wav.cpu(), model.sample_rate, strategy="loudness")
```

## Common Pitfalls

1. **GPU required** — AudioCraft models are large; CPU generation is very slow
2. **Duration limits** — MusicGen max generation is ~30s per call; extend with continuation
3. **Artifacts** — Vocals in music may have artifacts at longer durations
4. **Model size** — `musicgen-medium` (1.5B params) is good balance; `musicgen-large` (3.3B) needs 16GB+ VRAM

## Verification Checklist

- [ ] Model loads without errors
- [ ] Audio file generated and playable
- [ ] Audio matches the description
- [ ] Output at correct sample rate (32000 Hz for MusicGen)
