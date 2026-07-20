---
name: segment-anything-model
description: "Use when performing zero-shot image segmentation — click, box, or automatic segmentation with Meta's Segment Anything Model (SAM)."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [segmentation, computer-vision, sam, image-processing]
    related_skills: [comfyui]
---

# Segment Anything Model (SAM) — Zero-Shot Image Segmentation

## Overview

Meta's SAM (Segment Anything Model) performs zero-shot image segmentation. Given an image, it can segment any object by clicking on it (point prompt), drawing a box around it (box prompt), or segmenting everything automatically (all masks).

## When to Use

- Extracting objects from images (background removal)
- Counting objects in an image
- Creating masks for image editing pipelines
- Preparing training data for other vision models
- Interactive segmentation in applications

Do NOT use for: object classification (SAM only segments, it doesn't identify what it segments), real-time video segmentation (use a dedicated video model), or fine-grained instance segmentation (SAM masks can be coarse).

## Installation

```bash
pip install git+https://github.com/facebookresearch/segment-anything.git
pip install opencv-python pycocotools matplotlib
# Download checkpoint
wget https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth
```

## Automatic Mask Generation

```python
import cv2
import torch
import numpy as np
from segment_anything import sam_model_registry, SamAutomaticMaskGenerator

# Load model
sam = sam_model_registry["vit_h"](checkpoint="sam_vit_h_4b8939.pth")
sam.to("cuda")

# Create mask generator
mask_generator = SamAutomaticMaskGenerator(sam)

# Generate masks
image = cv2.imread("input.jpg")
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
masks = mask_generator.generate(image)

# masks is a list of dicts: {segmentation, area, bbox, predicted_iou, stability_score}
print(f"Generated {len(masks)} masks")
```

## Point-Prompt Segmentation

```python
from segment_anything import SamPredictor

predictor = SamPredictor(sam)
predictor.set_image(image)

# Segment at point coordinates (x, y) with a click
input_point = np.array([[500, 375]])
input_label = np.array([1])  # 1=foreground, 0=background

masks, scores, logits = predictor.predict(
    point_coords=input_point,
    point_labels=input_label,
    multimask_output=True,
)
```

## Common Pitfalls

1. **Large model** — SAM ViT-H is 2.4GB; use `vit_l` or `vit_b` for lower memory
2. **Image resolution** — SAM resizes to 1024x1024 internally; very small objects may be missed
3. **Over-segmentation** — Automatic mode may produce too many masks; adjust `pred_iou_thresh` and `stability_score_thresh`
4. **Edge quality** — SAM masks can be coarser than manual annotation

## Verification Checklist

- [ ] Model checkpoint downloaded
- [ ] At least one mask generated from an image
- [ ] Overlay visualization works correctly
- [ ] Chosen threshold produces useful results
