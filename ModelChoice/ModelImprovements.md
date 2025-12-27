# Model Improvements

## Overview

The current system is designed as a **working prototype** that prioritizes:
- Visual-only reasoning
- Explainability
- Cost-free reproducibility
- Clear system design
---

## Current Trade-offs

The existing implementation intentionally accepts certain trade-offs:

| Dimension | Current State |
|--------|--------------|
| Accuracy | Moderate (zero-shot models) |
| Latency | Medium–high (multi-stage pipeline) |
| Cost | Free |
| Explainability | High |
| Reproducibility | High |

These trade-offs were chosen deliberately to avoid reliance on paid APIs and black-box models.
---

## Improvement Areas

### 1. Learned Scoring Heads on CLIP Embeddings

**Current approach**
- Rule-based score calibration

**Improvement**
- Train small neural heads (MLP or linear layers) on top of CLIP embeddings
- Predict:
  - Gender expression
  - Visual weight
  - Embellishment

**Requirements**
- Small labeled dataset
- Still fully open-source

**Benefits**
- Higher accuracy
- Retains explainability

---

### 2. Improved Geometry Detection via Segmentation

**Current limitation**
- Frame geometry is ambiguous for thin or transparent objects

**Improvement**
- Integrate instance segmentation (e.g., SAM)
- Extract contours and structural features

**Benefits**
- More reliable geometry classification
- Reduced “ambiguous” outcomes

---

### 3.Paid Vision APIs 

**Potential**
- OpenAI GPT-4o Vision
- Google Gemini Vision

**Trade-offs**
- Higher accuracy
- Lower latency
- Paid access required
- Reduced transparency

**Decision**
- Not used to preserve cost-free, reproducible evaluation

---

## Validation Improvements

Future versions could include:
- Automated consistency checks
- Score variance monitoring across images
- Confidence intervals per dimension
- Regression tests on known products

---

