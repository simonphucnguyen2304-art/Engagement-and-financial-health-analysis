# Engagement and Financial Health Analysis

### Customer Segmentation for Consumer Finance

A data-driven customer segmentation project based on **financial health**, **customer engagement**, spending behavior, and transaction activity.

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Machine%20Learning-F7931E?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)

---

## Project Overview

This project analyzes customer engagement and financial health using a synthetic consumer finance dataset from Vietnam.

The main objective is to identify meaningful customer segments based on:

- Financial health
- Customer engagement
- Spending behavior
- Credit utilization
- Transaction frequency
- Digital spending activity
- Spending volatility
- Transaction recency
- Customer demographics

The analysis combines exploratory data analysis, data-quality validation, feature engineering, unsupervised learning, and customer profiling to support data-driven business decisions.

---

## Key Project Statistics

| Metric | Value |
|---|---:|
| Consumer-month records | **10,992** |
| Unique customers | **999** |
| Maximum observation period | **12 months** |
| Complete-history customers | **908** |
| Short-history customers | **91** |
| Geographic coverage | **34 provinces and cities** |
| Final customer segments | **6** |
| Random seed | **42** |

---

## Business Objectives

This project aims to answer the following business questions:

1. Which customers are financially healthy or financially vulnerable?
2. Which customers demonstrate high or low engagement?
3. What spending behaviors are associated with financial stress?
4. Which customer groups require financial monitoring?
5. Which segments are suitable for digital engagement campaigns?
6. How can customer segmentation support targeted financial products and services?

---

## Repository Structure

```text
Engagement-and-financial-health-analysis/
│
├── eda/
│   ├── ITB_Task_1.ipynb
│   ├── Task2.ipynb
│   ├── Task3.ipynb
│   └── testing.txt
│
├── model/
│   ├── model.ipynb
│   ├── customer_segmentation_preprocessed.csv
│   ├── customer_segment_mapping.csv
│   ├── segment_profile_summary.csv
│   ├── segment_demographic_detail.csv
│   ├── k_selection.png
│   └── testing.txt
│
├── report/
│   └── report.txt
│
└── README.md
```

---

## Dataset Description

The project uses a consumer financial health and engagement dataset containing monthly customer-level observations.

The dataset includes financial, behavioral, engagement, and demographic attributes such as:

### Financial Features

- Monthly income
- Credit limit
- Opening balance
- Ending balance
- Total spending
- Essential spending
- Discretionary spending
- Spend-to-income ratio
- Credit utilization ratio

### Engagement Features

- Transaction count
- Active transaction days
- Average transaction value
- Category diversity
- Transaction recency
- Online spending ratio
- Engagement score

### Customer Health Features

- Financial health score
- Financial health segment
- Next-month low-health flag
- Spending volatility

### Demographic Features

- Age
- Gender
- Occupation
- Province or city

---

## Analysis Pipeline

### 1. Exploratory Data Analysis

The EDA notebooks examine the structure, quality, consistency, and distribution of the dataset.

The analysis includes:

- Dataset shape and schema inspection
- Customer and monthly-record counting
- Duplicate-key detection
- Missing-value analysis
- NaN and infinite-value detection
- Customer-history validation
- Demographic consistency checks
- Spending-ratio validation
- Distribution analysis of financial and engagement variables

The dataset contains:

- **10,992 consumer-month records**
- **999 unique customers**
- An average of approximately **11 months of data per customer**
- **No duplicate consumer-month keys**
- **908 customers with complete 12-month histories**
- **91 customers with incomplete histories**

---

### 2. Data Quality Validation

The project performs several data-quality checks before building customer-level features.

The validation process checks:

- Whether each customer has sufficient monthly history
- Whether `(consumer_id, analysis_month)` is unique
- Whether financial ratios remain within valid ranges
- Whether demographic values are consistent
- Whether essential and discretionary spending ratios sum to one
- Whether missing values are expected or problematic
- Whether volatility can be calculated for each customer

Customers with fewer than 12 months of history are separated from customers with complete histories to avoid unreliable comparisons during segmentation.

---

### 3. Feature Engineering

Customer-level features are created from monthly observations.

Important features include:

| Feature | Description |
|---|---|
| `financial_health_score` | Overall financial health score from 0 to 100 |
| `engagement_score` | Overall customer engagement score from 0 to 100 |
| `essential_spend_ratio` | Percentage of spending allocated to essential needs |
| `online_spend_ratio` | Percentage of spending through online channels |
| `spend_to_income_ratio` | Spending pressure relative to income |
| `credit_utilization_ratio` | Proportion of available credit being used |
| `category_diversity` | Number of spending categories used |
| `transaction_recency_days` | Recency of the latest transaction |
| `spending_volatility` | Variation in the customer's spending behavior |

The feature-engineering process aggregates monthly behavior into customer-level profiles for clustering.

---

### 4. Customer Segmentation Model

The project uses unsupervised learning to group customers with similar financial and behavioral characteristics.

The main modeling steps include:

1. Selecting relevant financial and engagement features.
2. Removing redundant or unsuitable variables.
3. Aggregating monthly records at the customer level.
4. Scaling numerical features.
5. Testing different cluster counts.
6. Applying K-Means clustering.
7. Evaluating cluster quality using:
   - Silhouette score
   - Davies-Bouldin score
8. Using PCA and visualizations to interpret the resulting clusters.
9. Mapping technical clusters to meaningful business labels.

A fixed random seed of **42** is used to improve reproducibility.

---

## Final Customer Segments

The final model produces six customer segments:

| Segment | Customers | Share |
|---|---:|---:|
| Financially Stretched but Highly Engaged | 232 | 23.2% |
| Financially Healthy & Highly Engaged | 208 | 20.8% |
| Financially Healthy but Disengaged | 200 | 20.0% |
| Low Engagement & Financially Vulnerable | 177 | 17.7% |
| Emerging Digital Customers | 126 | 12.6% |
| Essential-Spend-Focused Customers | 56 | 5.6% |

---

## Segment Interpretation

### 1. Financially Stretched but Highly Engaged

These customers interact frequently and actively use financial products, but their spending pressure and credit utilization indicate potential financial stress.

Recommended business actions:

- Offer responsible credit-management support.
- Provide spending alerts and budgeting tools.
- Monitor changes in financial health.
- Avoid excessive promotion of additional borrowing.

---

### 2. Financially Healthy & Highly Engaged

These customers show strong engagement and relatively healthy financial behavior.

Recommended business actions:

- Offer premium financial products.
- Provide loyalty benefits.
- Promote investment and wealth-management services.
- Encourage long-term customer retention.

---

### 3. Financially Healthy but Disengaged

These customers are financially stable but have relatively low engagement or transaction recency.

Recommended business actions:

- Use personalized re-engagement campaigns.
- Recommend relevant products based on previous behavior.
- Improve digital communication.
- Introduce loyalty rewards and targeted offers.

---

### 4. Low Engagement & Financially Vulnerable

These customers demonstrate both weak engagement and relatively high financial pressure.

Recommended business actions:

- Monitor financial-health deterioration.
- Provide financial education and budgeting support.
- Use early-warning indicators for potential risk.
- Avoid aggressive credit-selling campaigns.

---

### 5. Emerging Digital Customers

These customers demonstrate a relatively high online-spending ratio but lower engagement with traditional financial activities.

Recommended business actions:

- Promote digital-first financial products.
- Improve mobile-app engagement.
- Offer personalized digital onboarding.
- Encourage recurring digital transactions.

---

### 6. Essential-Spend-Focused Customers

These customers allocate a relatively high proportion of spending to essential categories.

Recommended business actions:

- Offer practical payment and budgeting products.
- Provide essential-spending rewards.
- Develop cash-flow support services.
- Create stable and predictable financial solutions.

---

## Key Insights

The analysis highlights several important patterns:

- Customer segmentation should consider both **financial health** and **engagement**, rather than relying on a single score.
- Highly engaged customers may still experience financial stress if their spending pressure and credit utilization are high.
- Financially healthy customers may require re-engagement if their transaction activity declines.
- Digital-spending behavior can identify customers who are ready for digital financial products.
- Customers with incomplete histories should be handled separately from customers with a full 12-month history.
- Spending ratios and transaction behavior provide useful signals for customer profiling.
- Business-friendly segment labels make clustering results easier to interpret and apply.

---

## Model Outputs

The project generates the following outputs:

### `customer_segmentation_preprocessed.csv`

Customer-level features, cluster assignments, segment labels, and customer-history status.

### `customer_segment_mapping.csv`

Mapping between technical cluster identifiers and business-friendly segment names.

### `segment_profile_summary.csv`

Summary statistics for each customer segment, including:

- Financial health score
- Engagement score
- Spending ratios
- Credit utilization
- Category diversity
- Transaction recency
- Spending volatility
- Customer count
- Customer percentage

### `segment_demographic_detail.csv`

Detailed demographic and behavioral information for customers assigned to each segment.

### `k_selection.png`

Visualization used to support the selection of the number of clusters.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook
- Google Colab

---

## How to Run the Project

### 1. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 2. Open the Repository

```bash
git clone https://github.com/simonphucnguyen2304-art/Engagement-and-financial-health-analysis.git
cd Engagement-and-financial-health-analysis
```

### 3. Run the EDA Notebooks

Open the notebooks inside the `eda/` directory:

```text
eda/ITB_Task_1.ipynb
eda/Task2.ipynb
eda/Task3.ipynb
```

### 4. Run the Segmentation Model

Open:

```text
model/model.ipynb
```

The notebook performs:

- Data loading
- Data-quality validation
- Feature engineering
- Customer-level aggregation
- Feature scaling
- Cluster selection
- K-Means modeling
- Segment profiling
- Output generation

> The original notebook uses Google Drive and Google Colab paths. Update the dataset path when running the project locally.

---

## Reproducibility

The project uses:

```python
SEED = 42
```

Using a fixed random seed ensures that the clustering process can be reproduced more consistently.

---

## Contributors

This project was developed by:

- **Phan Vũ Đức Trung**
- **Bùi Minh Trung**
- **Đỗ Hoàng Quân**
- **Đăng Biên Phúc Lâm**
- **Huỳnh Phúc Nguyên**

---

## Project Status

Completed analytical project including:

- Exploratory data analysis
- Data-quality validation
- Feature engineering
- Customer-level aggregation
- K-Means customer segmentation
- Segment profiling
- Demographic analysis
- Business recommendations

---

## License

This repository is intended for educational, analytical, and portfolio purposes.

The dataset is a synthetic consumer finance case study. Any redistribution or commercial use of the underlying data should follow the terms provided by the dataset owner.

---

<div align="center">

Built with Python, customer analytics, and data-driven decision-making.

</div>
