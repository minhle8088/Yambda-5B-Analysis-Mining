# 📂 Data Provenance & Sampling Methodology

This directory provides documentation for the dataset used in the Yambda-5B Music Recommendation Analysis. Due to the large scale of the source data, the raw files are hosted externally, and a curated sample is used for the primary analysis.

## 🔗 Source Data
The primary dataset is **Yambda-5B**, a large-scale music streaming dataset provided by the Yandex.Music team. 
* **Official Citation:** Yandex.Music Team. (2025). *Yambda-5B: A Large-Scale Music Streaming Dataset for Research*. RecSys '25.
* **Source Link:** [https://arxiv.org/abs/2410.03840](https://arxiv.org/abs/2410.03840)
* **Access:** The raw dataset contains 5 billion interactions. For this project, we utilize the interaction logs specifically containing `uid` (User ID), `item_id` (Track ID), and `timestamp`.

## 🛠️ Sampling & Preprocessing
To ensure computational feasibility within a single-machine environment (Google Colab), the following sampling strategy was applied to generate the `yambda_sample.parquet` file used in the `main_notebook.ipynb`:

1. **Stratified User Sampling:** We extracted a random sample of 100,000 unique users to ensure a representative distribution of listening behaviors.
2. **Activity Filtering:** Users with fewer than 3 interactions were excluded to ensure the dataset was "Sequential Ready" for the PrefixSpan implementation.
3. **Feature Selection:** We retained only the essential columns for mining: `uid`, `item_id`, and `timestamp` (or `ts`).
4. **Storage Format:** The final sample was stored as a **Parquet** file to utilize columnar compression, reducing memory overhead during the FP-Growth and Sequential Pattern Mining phases.

## ⚠️ Accessing the Data for Reproducibility
The `.parquet` file used in the notebook is stored in a private Google Drive directory. To reproduce the results:
1. Access the Yambda-5B dataset via the official Yandex research links.
2. Apply the sampling logic described above.
3. Update the `file_path` variable in the first code cell of `main_notebook.ipynb` to point to your local version of the sampled data.
