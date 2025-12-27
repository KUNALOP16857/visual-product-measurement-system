# Visual Product Measurement System

## Overview

This project implements a **vision-enabled AI system** that analyzes product images and produces **structured, machine-readable visual measurements** derived exclusively from **observable appearance**.

The system avoids manual tagging and business-driven categorization. Instead, it relies on **computer vision and vision–language models** to extract objective, repeatable visual characteristics directly from product images.
---

## High Level Architecture Diagram
The Diagram is present in HighLevelArchitecture.png and all libraries explained in explained.md

## What the System Does
- Accepts **one or more images per product**
- Analyzes images using **vision-capable AI models**
- Produces **continuous visual measurements (−5.0 → +5.0)** across multiple dimensions
- Detects **clearly observable visual attributes**
- Exports results as:
  - Structured **JSON** 
  - A formatted **PDF report** 
---

## High-Level System Architecture

### 1. Input

- Excel-based product catalog
- Multiple image URLs per product

---

### 2. Processing Pipeline

#### (a) BLIP — Vision Captioning

- Generates natural-language visual descriptions from product images
- Used to surface high-level observable traits (materials, shape cues, style hints)
- Captions are generated per image and aggregated into a representative description

#### (b) CLIP — Vision–Semantic Reasoning

- Performs image–text similarity between product images and carefully designed visual prompts
- Used to infer:
  - Gender expression
  - Visual weight
  - Embellishment
  - Dominant color
  - Style-related cues
- Produces raw similarity signals that are later calibrated into standardized score ranges

#### (c) Pixel-Level Analysis (OpenCV)

- Extracts low-level visual features such as:
  - Brightness
  - Edge density
  - Aspect ratio
- Used to support:
  - Geometry inference
  - Transparency estimation
  - Texture classification
- Provides a complementary signal to semantic vision models

#### (d) Reasoning & Aggregation Layer

- Aggregates signals across **multiple images per product**
- Normalizes and scales raw model outputs into **−5.0 → +5.0** ranges
- Explicitly handles ambiguity rather than forcing overconfident predictions
- Produces deterministic, explainable measurements

---

### 3. Output

- `results.json` — structured, machine-consumable output (printed in the notebook)
- `visual_product_report.pdf` — a formatted, human-readable summary of results

---

## Key Assumptions and Design Decisions

### Vision-Only Reasoning

- All measurements are derived exclusively from visual evidence
- No product category, pricing, brand, or business metadata is used

### Hybrid Vision Approach

- No single model provides sufficient signal
- Combining:
  - Vision–language models (BLIP, CLIP)
  - Pixel-level analysis (OpenCV)
    improves robustness and explainability

### Multi-Image Aggregation

- Products often have multiple viewpoints
- Measurements are aggregated across images to reduce single-view bias

### Score Calibration

- Raw model similarity scores are not directly interpretable
- Scores are normalized and scaled into a standardized **−5.0 → +5.0** range

---

## AI Provider Considerations (OpenAI & Gemini)

The system was initially designed to be compatible with **vision-enabled LLM APIs such as OpenAI GPT-4V and Google Gemini Vision**. However:

- Both **OpenAI Vision** and **Gemini Vision APIs require paid API keys**
- Free-tier vision access is either unavailable or extremely limited
- API quotas and billing constraints make reproducible evaluation difficult

### Final Decision

To ensure:
- Cost-free execution
- Transparency of implementation
- No dependency on paid APIs
The final system uses **open-source vision models (BLIP + CLIP)**, which provide comparable vision understanding capabilities for this task.
This decision preserves the core requirement of **vision-enabled AI analysis** while ensuring the system can be run end-to-end without billing setup.

---

## Limitations

- Frame geometry inference for thin objects can be ambiguous
- Image quality and viewpoint diversity affect confidence
- Performance depends on the quality of vision-language prompts

---

## Tests and Validation Logic
The system uses lightweight validation logic to ensure consistency, robustness, and interpretability of outputs.
### Validation Checks

- **Score Range Enforcement**
  - All visual scores are clamped to the range −5.0 to +5.0
  - Prevents out-of-bound or unstable values

- **Deterministic Output**

  - Given the same images, the system produces consistent measurements
  - No stochastic sampling is used during inference

- **Multi-Image Consistency**

  - Measurements are aggregated across multiple images per product
  - Reduces bias from single viewpoints

- **Ambiguity Handling**

  - Frame geometry returns "ambiguous" when visual evidence is insufficient
  - Confidence scores are reduced when ambiguity is detected

- **Failure Handling**
  - Invalid or unreachable image URLs are skipped
  - Products with no valid images are ignored safely
---

## How to Run (Google Colab)

1. Open the notebook in **Google Colab**
2. Upload the Excel dataset
3. Run all cells top-to-bottom
4. Inspect structured JSON output in the notebook
5. Download the generated **PDF report**

---

## Setup Instructions (Local)

The project can be run locally using Python without requiring any paid API keys.

### Prerequisites

- Python 3.9 or higher
- Git
- Virtual environment tool (optional but recommended)

### Installation Steps

1. Clone the repository:

   ```bash
   git clone https://github.com/<your-username>/visual-product-measurement-system.git
   cd visual-product-measurement-system

   ```

2. Install dependencies:
   pip install -r requirements.txt

## Steps to Run the Assignment Locally (Jupyter)

1. Open the Jupyter notebook:

   ```bash
   jupyter notebook visual_product_measurement.ipynb

   ```

2. Update the Excel file path in the notebook if required.
3. Run all cells from top to bottom.
4. Inspect the structured JSON output printed in the notebook.
5. The formatted PDF report will be generated in the project directory.

## Technologies Used

- Python
- Google Colab
- BLIP (Vision Captioning)
- CLIP (Vision–Semantic Reasoning)
- OpenCV
- ReportLab

### Dependencies
All dependencies are listed in `requirements.txt`.  
The project uses only open-source libraries and does not require paid API keys.

Note: The notebook is optimized for GitHub rendering; interactive widgets are removed for compatibility.
