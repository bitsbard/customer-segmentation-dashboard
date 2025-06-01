# Customer Segmentation Dashboard

## Project Overview

A portfolio project to segment e-commerce customers using RFM analysis and visualize insights.

## Folder Structure

- `notebooks/` — Jupyter notebooks for each project phase
- `data/` — Raw and processed data files (e.g., CSVs)
- `ecommerce_data.db` — SQLite database for all data processing

## Phases

### Phase 1: Data Collection and Preparation
- **Notebook:** `notebooks/phase_1_data_collection.ipynb`
- **Goal:** Import e-commerce data into SQLite and explore its structure.
- **Output:** `data.csv` in `data/`, `transactions` table in SQLite.

### Phase 2: Data Cleaning and Preprocessing
- **Notebook:** `notebooks/phase_2_data_cleaning.ipynb`
- **Goal:** Remove duplicates, handle missing values, convert dates, and calculate total spend.
- **Output:** `transactions_clean` table in SQLite, `transactions_clean.csv` in `data/`.

### Phase 3: Calculating RFM Scores
- **Notebook:** `notebooks/phase_3_rfm_analysis.ipynb`
- **Goal:** Compute Recency, Frequency, and Monetary metrics for each customer.
- **Output:** `rfm` table in SQLite, `rfm.csv` in `data/`.

### Phase 4: Segmenting Customers
- **Notebook:** `notebooks/phase_4_segmentation.ipynb`
- **Goal:** Assign RFM-based scores and customer segments, validate segment distribution.
- **Output:** `rfm_segmented` table in SQLite, `rfm_segmented.csv` in `data/`.

### Phase 5: Data Visualization with Tableau

