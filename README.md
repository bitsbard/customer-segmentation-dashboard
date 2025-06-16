# Customer Segmentation Dashboard

## Project Overview

A data analysis portfolio project to segment e-commerce customers using RFM analysis and visualize insights.

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
- **Tableau Public Link:** [https://public.tableau.com/views/CustomerSegmentationDashboard](https://public.tableau.com/views/CustomerSegmentationDashboard_17488261585640/CustomerSegmentationDashboard?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
![](0.png)

## Analysis Report

### Executive Summary
This report analyzes the customer segmentation dashboard, which provides insights into customer distribution, purchasing behavior, and value across five segments: Others, Champions, At Risk, Loyal Customers, and Potential Loyalist. The data highlights significant variations in customer count, frequency, recency, and monetary contributions, offering actionable insights for targeted marketing and retention strategies.

### Key Findings
#### Customer Distribution (Customers per Segment)
The "Others" segment dominates with 3,374 customers (approximately 75% of the total), indicating a large, potentially untapped or inactive group.  
"Champions" (496 customers) and "At Risk" (320 customers) follow, with "Loyal Customers" (110) and "Potential Loyalist" (72) representing smaller but critical segments.  
Focus should be on converting "Others" into active segments and retaining "Champions" while addressing "At Risk" customers.

#### Frequency vs. Monetary Analysis
A scatter plot reveals "Champions" exhibit the highest frequency (up to 260 transactions) and monetary value (up to 250K), making them the most valuable segment.  
"Others" show moderate frequency but low monetary value, suggesting infrequent high-value purchases or inconsistent engagement.  
"At Risk" customers have declining frequency, indicating a need for re-engagement campaigns.  
"Loyal Customers" and "Potential Loyalist" show lower frequency and monetary contributions, requiring nurturing to increase value.

#### Recency Distribution
"At Risk" customers have the lowest recency (around 50 days), signaling urgent intervention to prevent churn.  
"Champions" and "Loyal Customers" show higher recency (around 200-300 days), reflecting consistent engagement.  
"Others" and "Potential Loyalist" have moderate recency, suggesting potential for activation with targeted offers.

#### Frequency Distribution
"Champions" lead with the highest frequency (up to 200 transactions), reinforcing their status as top performers.  
"At Risk" and "Loyal Customers" show moderate frequency (around 100-150), while "Others" and "Potential Loyalist" lag, indicating lower engagement levels.

#### Monetary Distribution
"Champions" contribute the highest monetary value (up to 200K), aligning with their high frequency and recency.  
"At Risk" customers show a wide range (up to 100K), suggesting past value that could be reclaimed.  
"Others," "Loyal Customers," and "Potential Loyalist" have lower monetary contributions (below 50K), highlighting opportunities for upselling or cross-selling.

### Recommendations
- **Retention Strategy:** Prioritize "At Risk" customers with personalized re-engagement campaigns to boost recency and prevent churn.  
- **Activation Strategy:** Target the "Others" segment with incentives to increase frequency and monetary value, converting them into "Champions" or "Loyal Customers."  
- **Nurturing Strategy:** Focus on "Potential Loyalist" and "Loyal Customers" with loyalty programs to enhance frequency and spending.  
- **Resource Allocation:** Invest heavily in "Champions" to maintain their high performance while monitoring their satisfaction to avoid future risk.

### Conclusion
The dashboard underscores the dominance of the "Champions" segment in driving value, the urgency of addressing "At Risk" customers, and the untapped potential in the "Others" group. Implementing the recommended strategies can optimize customer lifetime value and improve overall engagement.

### Next Steps
Review campaign performance metrics in 30 days to assess impact and adjust strategies accordingly.
