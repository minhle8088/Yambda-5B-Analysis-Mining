# Scalable Music Recommendation Analysis (Yambda-5B)

This repository contains the end-to-end data mining pipeline for analyzing large-scale music streaming interactions using the **Yambda-5B** dataset. This project focuses on comparing traditional course-based methodologies with advanced, industry-standard graph techniques.

## Project Overview

The primary goal is to extract meaningful patterns from 5 billion music streaming interactions to improve recommendation accuracy and understand user behavior. This project bridges the gap between foundational data mining and state-of-the-art machine learning by evaluating:

* **Course Foundations:** Frequent Itemset Mining and Association Rules to identify track co-occurrence.
* **Advanced Techniques:** Sequential Pattern Mining and **Lightweight Graph Neural Networks (LightGNN)** to model temporal user intent and graph-based relationships.

## Dataset Selection & Justification

After a comparative analysis of three candidate datasets (Yambda-5B, DUET Time Series, and HPDGNN Social Graphs), **Yambda-5B** was selected for its professional scale and analytical depth.

* **Scale:** 5 billion interactions, 1 million users, and 9.39 million tracks stored in partitioned Parquet files.
* **Technical Challenge:** The 85GB raw size necessitates the use of scalable data pipelines, strategic sampling, and efficient algorithms like FP-Growth.
* **Analytical Potential:** Allows for a direct comparison between unordered patterns (baskets) and temporal sequences.

## Current Progress: Checkpoint 1

The following milestones have been completed and are documented in `637005052_project_checkpoint_1.ipynb`:

### 1. Exploratory Data Analysis (EDA)

* **Popularity Bias:** Identified a heavy "Long Tail" distribution where a small subset of tracks dominates total interaction volume, motivating the need for GNNs to improve "niche" recommendations.
* **Temporal Burstiness:** Analyzed inter-event gaps, discovering that most interactions occur in rapid "bursts" (typically <5 minutes apart), which confirms a strong session-based structure.
* **Sparsity Analysis:** Evaluated item co-occurrence sparsity to determine appropriate support and confidence thresholds for association rule mining.

### 2. Professional Integrity & Validation

To ensure industrial-grade robustness, the pipeline includes an **Automated Integrity Audit** consisting of:

* **Temporal Logic Checks:** Validating that engineered time-gaps adhere to causality.
* **Structural Coverage:** Ensuring that 10% fractional sampling maintains the statistical diversity of the original item space.
* **Schema Validation:** Automated verification of data types and required features (uid, item_id, timestamp).

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
