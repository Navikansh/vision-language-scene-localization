# Scene Localization in Dense Images via Natural Language Queries

**Goal:** Given a dense image and a natural language query (e.g., *"a person snatching a chain"*), the system identifies and crops the region of the image that best matches the described scene.

---

## Features
- **Natural Language Understanding**: Uses CLIP embeddings to align text and image features.
- **Multiple Approaches Implemented**:
  1. **YOLO-based Detection** – Fast object localization using pre-trained YOLO models.
  3. **CMA-ES Multi-Frame Search** – Optimizes multiple candidate frames simultaneously using evolutionary strategies.
  4. **Attention-Augmented Frame Scoring** – (Under Progress) Improves localization by weighting features with attention.

---

## Approach Overview

### YOLO-Based Approach
- Detects objects using YOLOv8/YOLOv5 (configurable).
- Selects detected regions that have the highest semantic similarity to the query text.

### CMA-ES Multi-Frame Optimization
- **Idea:** Maintain multiple candidate frames and evolve them to maximize similarity.
- **Method:** Uses `cma.CMAEvolutionStrategy` to optimize `(x, y, w, h)` of each frame.


### Attention-Weighted Frame Selection *(Under Progress)*
- Integrates attention maps from CLIP's vision encoder.
- Prioritizes regions containing the most query-relevant features.
