# Food and Beverage Analysis Across All US States

This repository analyzes monthly percent-change trends in the Food & Beverage retail sector across all U.S. states—examining COVID-19 impacts, seasonal patterns, regional clusters, policy correlations, and forecasting future trends.

##  Project Overview

The core of this analysis is a Jupyter Notebook that:
- **Labels** time periods (pre-COVID, COVID, post-COVID) and compares average percent-change in F&B store sales across them.
- Identifies **top-performing and worst-performing states** during 2020, and explores their correlation with policy measures—such as alcohol store openings, mask mandate enforcement, and stay-at-home duration.
- Detects **seasonal and structural patterns** using hierarchical clustering at the state and regional levels.
- Builds a **6-month forecast** for Washington state using ARIMA modeling with data transformation and outlier handling.

## Repository Structure

├── COVID-19 Alcohol.csv
├── COVID-19 Face Masks.csv
├── COVID-19 Stay at Home.csv
├── Food-&-Beverage-stores.csv
├── notebook.ipynb
└── README.md ← You’re here

- `COVID-19 … .csv`: Contain COVID-era policy datasets (alcohol store openings, mask mandates, stay-at-home orders).
- `Food-&-Beverage-stores.csv`: Daily/monthly percent changes in F&B store sales by state.
- `notebook.ipynb`: The Jupyter notebook executing the full analysis pipeline.

## How to Use This Repository

### 1. Clone the repo
```bash
git clone https://github.com/DiaHere/Food-and-Beverage-across-all-US-states-Analysis.git
cd Food-and-Beverage-across-all-US-states-Analysis

### 2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels pmdarima

