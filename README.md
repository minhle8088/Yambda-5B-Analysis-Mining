# 🎵 Scalable Music Recommendation Analysis (Yambda-5B)

> Uncovering patterns in 5 billion music streaming interactions using data mining and graph-based techniques.

👉 **Start here: [main_notebook.ipynb](./main_notebook.ipynb)**

🎥 **Project Video:** https://youtu.be/xqGl4UwkVHk

---

## Overview

This project applies end-to-end data mining to the **Yambda-5B** dataset — an industrial-scale collection of 5 billion music listening events from Yandex.Music. The goal is to compare traditional course-based methodologies with advanced, industry-standard graph techniques to improve music recommendation quality and understand user behavior at scale.

We evaluate two families of approaches:
- **Course Foundations:** Frequent Itemset Mining and Association Rules to identify track co-occurrence patterns
- **Advanced Techniques:** Sequential Pattern Mining and **Lightweight Graph Neural Networks (LightGNN)** to model temporal user intent and graph-based relationships

---

## Research Questions

1. How do varying support thresholds affect the diversity of discovered rules in a dataset with extreme popularity bias?
2. To what extent do sequential patterns reveal genre transitions that are lost when treating sessions as unordered baskets?
3. Can LightGNN embeddings effectively generalize across the "Long Tail" more accurately than standard association rules?

---

## Results Summary

- Discovery of "Gateway Tracks": Sequential mining revealed tracks that serve as high-probability entry points into specific genres, which static association rules categorized merely as "popular."

- Non-Triviality Proof: Our analysis isolated patterns that occur twice as often as expected by chance, providing a more robust foundation for recommendation engines than simple popularity metrics.
---

## Repo Structure

```
Yambda-5B-Analysis-Mining/
├── main_notebook.ipynb          # 👈 Main deliverable — start here
├── requirements.txt             # Full package list from Colab environment
├── .gitignore
├── README.md
├── checkpoints/
│   ├── checkpoint_1.ipynb       # Project Checkpoint 1 — EDA & scoping
│   └── checkpoint_2.ipynb       # Project Checkpoint 2 — [add description]
├── src/                         # Data processing & helper scripts
│   └── [your scripts here]
└── data/
    └── README_data.md           # Instructions for downloading the dataset (not committed — too large)
```

---

## Dataset

**Yambda-5B** is an industrial-scale dataset released by Yandex.Music for the RecSys 2025 Dataset & Benchmark Track.

| Attribute | Value |
|---|---|
| Total interactions | 5 Billion |
| Users | 1 Million |
| Unique tracks | 9.39 Million |
| Format | Partitioned Parquet files |
| Raw size | ~85 GB |

### How to Get the Data

The dataset is **not included** in this repo due to size. To reproduce the analysis:

1. Visit the official [Yambda dataset on Hugging Face](https://huggingface.co/datasets/yandex/yambda)
2. Download `listens.parquet` from the `flat/50m` subfolder (50M-interaction sample)
3. Rename it to `yambda_sample.parquet` and place it in the `data/` directory

---

## How to Reproduce

This project was built in **Google Colab** using Python 3.11.

1. Clone the repo:
```bash
   git clone https://github.com/minhle8088/Yambda-5B-Analysis-Mining.git
```
2. Download the dataset and place it in `data/` (see above)
3. Install dependencies:
```bash
   pip install -r requirements.txt
```
4. Run in order:
   - `checkpoints/checkpoint_1.ipynb` — EDA and data exploration
   - `checkpoints/checkpoint_2.ipynb` — Intermediate analysis
   - `main_notebook.ipynb` — Full pipeline and final results

---

## Key Dependencies

| Package | Version |
|---|---|
| Python | 3.11 |
| pandas | *(from requirements.txt)* |
| numpy | *(from requirements.txt)* |
| matplotlib | *(from requirements.txt)* |
| seaborn | *(from requirements.txt)* |
| pyarrow | *(from requirements.txt)* |

> Full environment is in [`requirements.txt`](./requirements.txt).

---

*Developed by Minh Le — Spring 2026*
