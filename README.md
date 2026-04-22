# Customer Segmentation Dashboard

**This e-commerce analysis identifies that while 75% of the customer base (3,374 users) is currently inactive or "At Risk," a high-value core of 496 "Champions" drives disproportionate revenue with individual spends reaching up to $279K. By implementing RFM (Recency, Frequency, Monetary) modeling via SQLite and Tableau, this project uncovers specific "Win-Back" opportunities within the inactive segments that could reclaim significant lost market share.**

> **View Dashboard:** [Tableau Public Report](https://public.tableau.com/views/CustomerSegmentationDashboard_17488261585640/CustomerSegmentationDashboard?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

---

## Business Problem

The marketing team lacks a data-driven way to distinguish between high-value loyalists and one-time shoppers, resulting in inefficient "one-size-fits-all" email campaigns. This analysis aims to solve:

1. **Retention Leakage** — Identifying "At Risk" customers before they churn permanently.
2. **Value Concentration** — Quantifying the revenue impact of top-tier "Champions."
3. **Targeting Precision** — Moving "Potential Loyalists" into higher-frequency tiers.

---

## Scope Limits

| In Scope | Out of Scope |
|---|---|
| RFM Segmentation (Recency, Frequency, Monetary) | Predictive Churn Modeling (ML-based) |
| SQL-based data cleaning and transformation | Product Recommendation Engine |
| Descriptive statistical analysis of segments | Seasonal forecasting |
| Interactive Dashboarding (Tableau) | Marketing channel attribution |

---

## Core Metrics Defined

| Metric | Definition |
|---|---|
| **Recency (R)** | Days since the customer's last purchase (lower is better) |
| **Frequency (F)** | Total number of distinct transactions per customer |
| **Monetary (M)** | Total lifetime spend (Sum of `unit_price * quantity`) |
| **RFM Score** | Weighted concatenation of R, F, and M rankings (1-5 scale) |
| **Champions** | High F, High M, and Low R (Most valuable and active) |
| **At Risk** | High F and M in the past, but High R (Haven't bought recently) |
| **Others** | High R and Low F (Largest group; mostly inactive or one-time buyers) |

---

## Dataset

**Source:** E-commerce Transactional Data

| Table | Description | Key Columns |
|---|---|---|
| `transactions` | Raw sales data | `InvoiceNo`, `StockCode`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID` |
| `transactions_clean` | Processed data | Added `TotalSpend`, cleaned `CustomerID`, standardized `Dates` |
| `rfm` | Aggregated metrics | `Recency`, `Frequency`, `Monetary` per `CustomerID` |
| `rfm_segmented` | Final output | Added `RFM_Score` and `Segment_Label` |

---

## Tech Stack

| Layer | Tool |
|---|---|
| Database | SQLite |
| Processing | Python (Pandas, SQLAlchemy) |
| Visualization | Tableau Desktop / Public |
| Environment | Jupyter Notebooks |
| Version Control | GitHub |

---

## Analysis Workflow

The project is structured into five sequential phases executed via Jupyter Notebooks.

| Phase | Notebook | Key Actions |
|---|---|---|
| **1. Collection** | `phase_1_data_collection.ipynb` | Import CSV to SQLite; initial schema inspection |
| **2. Cleaning** | `phase_2_data_cleaning.ipynb` | Handle nulls; remove returns; calculate `TotalSpend` |
| **3. RFM Calculation**| `phase_3_rfm_analysis.ipynb` | SQL aggregations to find R, F, and M per user |
| **4. Segmentation** | `phase_4_segmentation.ipynb` | Binning metrics; assigning segment labels (Champions, etc.) |
| **5. Visualization** | `Tableau Dashboard` | Interactive scatter plots and distribution boxplots |

### Key SQL Patterns Used

**Calculating RFM Metrics:**
```sql
SELECT 
    CustomerID,
    CAST(JULIANDAY('2011-12-10') - JULIANDAY(MAX(InvoiceDate)) AS INT) AS Recency,
    COUNT(DISTINCT InvoiceNo) AS Frequency,
    SUM(Quantity * UnitPrice) AS Monetary
FROM transactions_clean
GROUP BY CustomerID;
```

**Segment Logic (Python/Pandas):**
```python
# Simplified quintile ranking
rfm['R_rank'] = pd.qcut(rfm['Recency'], 5, labels=[5, 4, 3, 2, 1])
rfm['F_rank'] = pd.qcut(rfm['Frequency'].rank(method='first'), 5, labels=[1, 2, 3, 4, 5])
rfm['M_rank'] = pd.qcut(rfm['Monetary'], 5, labels=[1, 2, 3, 4, 5])
```

---

## Key Findings

| Finding | Detail |
|---|---|
| **Customer Distribution** | **75%** of customers fall into "Others," highlighting a massive re-engagement gap. |
| **Revenue Concentration** | Champions drive the highest value, with outliers spending up to **$279K**. |
| **Recency Gap** | "At Risk" and "Others" show median recency **>100 days**, indicating a high lapse rate. |
| **Engagement Trend** | Most customers have low frequency; high-frequency outliers are concentrated in "Champions." |
| **Opportunity** | "Potential Loyalists" (72 users) have low recency but low spend; they are primed for upselling. |

---

## Recommendations

* **Nurture Champions:** Implement a VIP loyalty program with exclusive rewards to prevent fatigue.
* **Reactivate "At Risk":** Use personalized "We Miss You" discounts based on their specific past purchase history.
* **Upsell Potential Loyalists:** Focus on bundle deals or "Frequent Buyer" points to increase their Frequency score.
* **Filter "Others":** Segment this group further; target high-monetary outliers for high-touch re-engagement while ignoring low-value/high-recency leads to save marketing spend.

---

## Repository Structure

```
customer-segmentation-rfm/
├── data/                        # Raw and processed CSV files
├── notebooks/                   # Phase 1-4 Jupyter Notebooks
│   ├── phase_1_data_collection.ipynb
│   ├── phase_2_data_cleaning.ipynb
│   ├── phase_3_rfm_analysis.ipynb
│   └── phase_4_segmentation.ipynb
├── ecommerce_data.db            # SQLite database file
└── README.md                    # Project documentation
```

---
