# Experience Working on This Problem

Working on this assignment was a valuable exercise in designing a practical, vision-based AI system rather than integrating paid OpenAI Vision APIs or Gemini Vision APIs.

One of the main challenges was dealing with the inherent ambiguity of visual understanding, especially for products like eyeglasses where attributes such as frame geometry, transparency, and style can be subtle and viewpoint-dependent. This required careful handling of uncertainty instead of forcing confident but potentially incorrect predictions.

Another important learning was the need to combine multiple sources of visual evidence. Vision-language models alone were insufficient for reliable measurements, so semantic reasoning (CLIP) was complemented with pixel-level analysis (OpenCV) and multi-image aggregation to improve robustness and consistency.

Practical constraints also influenced design decisions. Vision APIs from providers like OpenAI and Google Gemini require paid access, which led to the adoption of open-source vision models to ensure reproducibility and cost-free execution while still meeting the core requirements of vision-enabled analysis.

Overall, the problem closely resembled real-world AI engineering work, involving trade-offs between accuracy, explainability, cost, and system design. It reinforced the importance of modularity, transparency, and defensible reasoning in building applied AI systems.
