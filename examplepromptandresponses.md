## Example Prompts and Responses

Although the system does not rely on a conversational LLM interface, it uses structured vision prompts internally for semantic reasoning via vision–language models.

### Example Vision Prompts (CLIP)

**Gender Expression**

- "masculine eyeglasses"
- "unisex eyeglasses"
- "feminine eyeglasses"

**Visual Weight**

- "thin lightweight eyeglasses"
- "bold heavy eyeglasses"

**Embellishment**

- "simple minimalist eyeglasses"
- "ornate decorative eyeglasses"

**Frame Geometry**

- "round eyeglasses"
- "rectangular eyeglasses"
- "square eyeglasses"
- "cat-eye eyeglasses"

The system computes image–text similarity scores and uses their relative differences as visual signals.

### Example Input (BLIP Caption)

"a pair of black metal eyeglasses on a white background"

### Example Structured Output

```json
{
  "product_id": 231031,
  "image_count": 3,
  "visual_description": "black metal rectangular",
  "analysis": {
    "scores": {
      "gender_expression": -2.5,
      "visual_weight": 1.8,
      "embellishment": -1.2,
      "unconventionality": 0.5,
      "formality": 1.5
    },
    "attributes": {
      "wirecore": true,
      "frame_geometry": "rectangular",
      "transparency": "opaque",
      "dominant_colors": ["black"],
      "textures": ["smooth"],
      "suitable_for_kids": false
    },
    "confidence": 0.85,
    "notes": "Derived exclusively from observable visual characteristics."
  }
}
```
