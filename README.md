# Scalable Music Recommendation Analysis (Yambda-5B)

This repository contains the end-to-end data mining pipeline for analyzing large-scale music streaming interactions using the **Yambda-5B** dataset. This project focuses on comparing traditional course-based methodologies with advanced, industry-standard graph techniques.

## Project Overview

The primary goal is to extract meaningful patterns from 5 billion music streaming interactions to improve recommendation accuracy and understand user behavior. This project bridges the gap between foundational data mining and state-of-the-art machine learning by evaluating:

* **Course Foundations:** Frequent Itemset Mining and Association Rules to identify track co-occurrence.
* **Advanced Techniques:** Sequential Pattern Mining and **Lightweight Graph Neural Networks (LightGNN)** to model temporal user intent and graph-based relationships.

## Dataset Overview & Acquisition

### 1. Dataset Overview

The project utilizes the **Yambda-5B** dataset, an industrial-scale collection provided by Yandex.Music for the **RecSys 2025 Dataset & Benchmark Track**.

* **Total interactions:** 5 Billion
* **Entities:** 1 Million users and 9.39 Million unique tracks
* **Format:** Partitioned Parquet files

### 2. How to Obtain the Data

Due to size constraints (85GB raw), the dataset is not hosted in this repository. To reproduce this analysis:

1. Visit the official [RecSys 2025 Dataset Track](https://recsys.acm.org/recsys25/) or the official [Yandex Yambda Hugging Face repository](https://huggingface.co/datasets/yandex/yambda).
2. Download the `listens.parquet` file from the `flat/50m` subfolder for a manageable 50-million-interaction sample.
3. Rename the file to `yambda_sample.parquet` and place it in your local `/data` directory.

### 3. Local Environment Setup

A `.gitignore` is included to prevent accidental uploads of large data files. Ensure your local folder structure matches the following:

```text
├── README.md
├── .gitignore
├── notebooks/
│   └── 637005052_project_checkpoint_1.ipynb
└── data/
    └── yambda_sample.parquet  <-- Place downloaded sample here

```

## Current Progress: Checkpoint 1

The following milestones have been completed and are documented in `notebooks/637005052_project_checkpoint_1.ipynb`:

### Exploratory Data Analysis (EDA)

* **Popularity Bias:** Identified a heavy "Long Tail" distribution where a small subset of tracks dominates total interaction volume, motivating the need for GNNs to improve "niche" recommendations.
* **Temporal Burstiness:** Analyzed inter-event gaps, discovering that most interactions occur in rapid "bursts" (typically <5 minutes apart), confirming a strong session-based structure.
* **Sparsity Analysis:** Evaluated item co-occurrence sparsity to determine appropriate thresholds for association rule mining.

## Professional Integrity Audit

The analysis pipeline includes a custom validation suite to ensure data quality after fractional sampling:

* **Temporal Logic:** Verifies that engineered inter-event gaps are non-negative to adhere to causality.
* **Diversity Check:** Ensures sampling preserves a significant track population (>1,000 unique items) to avoid biased results.
* **Schema Check:** Automated verification of data presence and types for critical fields (`uid`, `item_id`, `timestamp`).

## Tech Stack

* **Language:** Python
* **Libraries:** Pandas, NumPy, Matplotlib, Seaborn
* **Data Engineering:** PyArrow (Parquet engine), Google Colab/Drive integration
* **Modeling Focus:** Frequent Itemsets, Sequential Mining, Graph Neural Networks (LightGNN)

## Research Questions

1. How do varying support thresholds affect the diversity of discovered rules in a dataset with extreme popularity bias?
2. To what extent do sequential patterns reveal genre transitions that are lost when treating sessions as unordered baskets?
3. Can LightGNN embeddings effectively generalize across the "Long Tail" more accurately than standard association rules?

---

*Developed by Minh Le — February 2026*
