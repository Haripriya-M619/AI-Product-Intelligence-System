
# AI Product Intelligence System
### Gen AI Bootcamp — Day 2 assignment | AlgoUniversity

An AI-powered Product Intelligence System for e-commerce built using 
Vision-Language Models. This project was developed as part of the 
Gen AI Bootcamp Day 2 assignment.

---

## Overview

Modern e-commerce platforms need more than just keyword search. 
This system uses CLIP (Contrastive Language-Image Pretraining) to 
understand products from images and enables three advanced AI features 
on top of a semantic similarity search engine.

---

## Dataset

- **Source:** Fashion Product Images Small (Myntra Dataset)
- **Total Products:** 44,419
- **Attributes:** Product ID, Category, Sub-category, Color, Product Name, Image

---

## System Architecture

```
Product Image
      │
      ▼
CLIP (ViT-B/32)
      │
Image Embeddings (512-dim)
      │
 ┌────┴────────┬────────────┐
 ▼             ▼            ▼
Task 1       Task 2       Task 3
Recommendation  Duplicate   Reverse
Engine       Detection    Text Search

Text Query → CLIP Text Encoder → Task 3
```

---

## Tasks

### ✅ Task 1 — Smart Product Recommendation Engine

**Problem:** E-commerce platforms recommend products commonly 
purchased together, not just visually similar products.

**Approach:** Rule-based category mapping using product metadata.

**Example:**
- Input: Running Shoes
- Output: Sports Socks, Fitness Watch, Water Bottle

**Why:** The dataset has no purchase history, so a knowledge-based 
mapping is used — the same approach used by early Amazon recommendation 
systems.

---

### ✅ Task 2 — Unique Product Catalog Creation

**Problem:** Large marketplaces contain duplicate or near-duplicate 
products uploaded by different sellers.

**Approach:** CLIP embeddings + DBSCAN clustering

**Steps:**
1. Generate 512-dim embedding for each product image using CLIP
2. Compute cosine similarity between embeddings
3. Apply DBSCAN to group near-duplicate products
4. Keep one representative product per cluster

**Results:**
- Duplicate groups detected: 20
- Unique catalog size: 147

---

### ✅ Task 3 — Reverse Product Search

**Problem:** Allow users to search products using text instead of images.

**Approach:** CLIP Text Encoder + Cosine Similarity

**Example:**
- Input: "blue casual shirt"
- Output: Top 5 matching product images

**Why CLIP:** CLIP encodes both images and text into the same 
512-dimensional embedding space, enabling direct comparison between 
text queries and product images.

---

## Tech Stack

| Component | Technology |
|---|---|
| Vision-Language Model | CLIP (ViT-B/32) |
| Similarity Metric | Cosine Similarity |
| Duplicate Detection | DBSCAN |
| Deep Learning Framework | PyTorch |
| Model Library | HuggingFace Transformers |
| Data Processing | Pandas, NumPy |
| Visualization | Matplotlib |

---

## Results

### Task 1: Smart Recommendation
<img width="1260" height="328" alt="Screenshot 2026-06-29 162014" src="https://github.com/user-attachments/assets/a2c26aa9-ffb6-4f20-836f-dbadca37e38e" />
<img width="1253" height="657" alt="Screenshot 2026-06-29 162030" src="https://github.com/user-attachments/assets/8666c380-52ce-462d-b0cd-6c3d191f419f" />
<img width="1238" height="643" alt="Screenshot 2026-06-29 162047" src="https://github.com/user-attachments/assets/47b956be-1251-4800-a6fd-cab34267fc6e" />



### Task 2: Duplicate Detection
<img width="1228" height="393" alt="Screenshot 2026-06-29 161930" src="https://github.com/user-attachments/assets/5a493d22-ce93-4280-8804-5826f40b8913" />
<img width="1244" height="619" alt="Screenshot 2026-06-29 161950" src="https://github.com/user-attachments/assets/863b2e65-00e5-4a6e-863d-8b6155f0b60e" />


### Task 3: Reverse Text Search
<img width="1017" height="653" alt="Screenshot 2026-06-29 161909" src="https://github.com/user-attachments/assets/f7961aaa-4e73-4083-a378-d62a4cfcd588" />
<img width="1282" height="333" alt="Screenshot 2026-06-29 161826" src="https://github.com/user-attachments/assets/d2092bdf-b7a0-4ffd-b17f-5c2cb07aa1a5" />

### Also detects similar choices
<img width="1301" height="384" alt="Screenshot 2026-06-29 161800" src="https://github.com/user-attachments/assets/088fed44-e4c0-4ce3-9d8f-8e8173daaf48" />

### Overall system
<img width="1113" height="551" alt="Screenshot 2026-06-29 162103" src="https://github.com/user-attachments/assets/199d491d-4256-4b6c-bb0d-f5f87f3dde8d" />

---

## Key Concepts Learned

- **CLIP** maps both images and text into the same embedding space
- **Cosine Similarity** measures semantic closeness between vectors
- **DBSCAN** clusters near-duplicate products without knowing 
  the number of groups beforehand
- **Reverse Search** enables text-to-image retrieval without 
  any keyword labels on products

---

## About

This project was built as part of **Gen AI Bootcamp — Day 2** assignment from AlgoUniversity.
The bootcamp focuses on practical applications of Generative AI and 
Vision-Language Models in real-world scenarios.
```

