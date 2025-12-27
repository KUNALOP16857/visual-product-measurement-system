## Core Deep Learning & Vision Models

### 1. `torch`
**Purpose:** Core deep learning framework  
- Provides tensor operations and GPU acceleration
- Required by both BLIP and CLIP models

---

### 2. `torchvision`
**Purpose:** Image preprocessing and transformations  
- Handles image normalization and resizing
- Provides utilities for preparing images for vision models

---

### 3. `transformers`
**Purpose:** Vision-language model support (BLIP)  
- Used to load and run the BLIP image captioning model
- Enables conversion of raw images into semantic visual descriptions
- Maintained by Hugging Face and widely adopted in research and industry
- 
---

### 4. `CLIP`
**Purpose:** Vision–semantic reasoning  
- Performs image–text similarity comparisons
- Enables zero-shot inference for:
  - Gender expression
  - Visual weight
  - Embellishment
  - Dominant color
- Allows continuous scoring without labeled training data

---

## Data Handling & Numerical Processing

### 5. `pandas`
**Purpose:** Excel and tabular data handling  
- Reads the product catalog from Excel files
- Manages product metadata and image URLs

---

### 6. `numpy`
**Purpose:** Numerical computation  
- Used for score normalization and aggregation
- Supports statistical operations across multiple images

---

## Pixel-Level Computer Vision

### 7. `opencv-python`
**Purpose:** Low-level visual analysis  
- Extracts pixel-based features such as:
  - Brightness
  - Edge density
  - Aspect ratio
- Supports geometry, transparency, and texture inference

---

### 8. `pillow`
**Purpose:** Image loading and manipulation  
- Downloads and decodes images from URLs
- Converts images into formats compatible with vision models and OpenCV

---

## Utility Libraries

### 9. `tqdm`
**Purpose:** Progress visualization  
- Displays progress bars during batch processing
- Improves usability and debugging for longer runs

---

### 10. `ftfy`
**Purpose:** Text normalization (CLIP dependency)  
- Fixes text encoding issues
- Ensures consistent text processing during CLIP inference

---

### 11. `regex`
**Purpose:** Text processing  
- Supports structured parsing of captions
- Used in normalization and rule-based reasoning logic

---

## Output & Reporting

### 12. `reportlab`
**Purpose:** Stylish PDF generation  
- Creates a human-readable PDF report
- Formats visual measurements and attributes cleanly
- Enables export beyond raw JSON outputs

---


All libraries are **open-source**, widely adopted, and require **no paid API keys**.


