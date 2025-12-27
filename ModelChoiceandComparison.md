# Model Choice and Comparison

## Overview

## This project intentionally uses a combination of **open-source vision models (BLIP, CLIP)** and **classical computer vision (OpenCV)** instead of relying on paid, black-box vision APIs.

## Why Not Paid Vision APIs (OpenAI / Gemini)?

### OpenAI Vision (GPT-4V / GPT-4o)

- Requires **paid API access**
- Free-tier vision access is unavailable or extremely limited
- Closed, black-box reasoning
- Hard to reproduce results without billing setup

### Google Gemini Vision

- Requires **Google Cloud billing**
- Free quota for vision is minimal or zero
- API rate limits complicate experimentation
- Outputs are less controllable for deterministic scoring

### Key Trade-offs

| Aspect               | Paid Vision APIs | This Project       |
| -------------------- | ---------------- | ------------------ |
| Cost                 | Paid             | Free               |
| Reproducibility      | Requires billing | Fully reproducible |
| Transparency         | Black-box        | Explainable        |
| Control over scoring | Limited          | Full               |
| Dependency risk      | High             | Low                |

## **Decision:** Paid APIs were avoided to ensure everyone could run and inspect the system without financial or quota barriers.

## Why BLIP + CLIP + OpenCV?

### BLIP (Vision Captioning)

- Converts raw images into **human-readable visual descriptions**
- Helps surface high-level, observable traits (material, style cues)
- Acts as a semantic bridge between vision and reasoning

### CLIP (Vision–Language Reasoning)

- Provides **image–text similarity scoring**
- Enables continuous, interpretable signals for:
  - Gender expression
  - Visual weight
  - Embellishment
  - Style cues
- Works well without task-specific fine-tuning

### OpenCV (Pixel-Level Analysis)

- Adds **grounded visual evidence**:
  - Brightness
  - Edge density
  - Aspect ratio
- Supports geometry, transparency, and texture inference
- Improves robustness where vision-language models are ambiguous

### Combined Strength

No single model is sufficient on its own.  
The hybrid approach allows:

- Semantic understanding (BLIP + CLIP)
- Low-level visual grounding (OpenCV)
- Explicit reasoning and aggregation

---

## Comparison with Other Free Vision Models

| Model                | Strengths             | Limitations                        |
| -------------------- | --------------------- | ---------------------------------- |
| YOLO / Detectron     | Object detection      | Not suited for style or aesthetics |
| ViT (classification) | Global features       | Requires labeled classes           |
| SAM                  | Segmentation          | No semantic interpretation         |
| BLIP                 | Captioning            | Not numeric by itself              |
| CLIP                 | Semantic similarity   | Needs calibration                  |
| **This system**      | Balanced, explainable | Slightly higher latency            |

**Decision:** A modular hybrid pipeline offers the best balance for appearance-based measurement.

---

## Alignment with Assignment Requirements

| Requirement               | How It Is Addressed         |
| ------------------------- | --------------------------- |
| Vision-enabled AI         | BLIP + CLIP                 |
| Continuous scores         | CLIP similarity calibration |
| Appearance-only reasoning | No metadata or labels used  |
| Multi-image support       | Aggregation layer           |
| Ambiguity handling        | Explicit modeling           |
| Structured output         | JSON + PDF                  |
| Cost awareness            | Open-source only            |

---

## Key Design Philosophy

- **Explainability over raw accuracy**
- **Engineering clarity over black-box APIs**
- **Visual evidence over inferred intent**

---
