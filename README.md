# COVID-19 Impact on U.S. Food & Beverage Sales
author: Dia Dana

## About

This project analyzes the impact of COVID-19 on **U.S. food and beverage retail sales**, measured as **month-to-month percent change in sales**, at the state level.

Using a combination of **policy data**, **time-series analysis**, **clustering**, and **forecasting**, the project investigates how consumer behavior shifted during the pandemic, whether government policies influenced sales outcomes, and how seasonal patterns evolved post-COVID.

Across stable years, **average national sales growth hovers around 4%**, while the COVID panic period stands out as a **structural break**, with growth exceeding **10% nationwide**.

---

## Key Questions

1. **COVID-19 Impact**
   - How did food & beverage sales change *pre-COVID → COVID → post-COVID*?
   - Which states experienced the largest sales spikes or declines during 2020?

2. **Policy Correlations**
   - Did alcohol store openings, mask mandates, or stay-at-home duration correlate with sales outcomes?
   - If so, how strong were these effects?

3. **Seasonal & Regional Patterns**
   - Do states share common seasonal consumption profiles?
   - Which states failed to return to pre-COVID seasonal behavior?
   - Do seasonal patterns align with geography?

4. **Forecasting**
   - Can we predict the next 6 months of sales trends for Washington State?
   - Which forecasting approach is most accurate?

---

## Methodology

### Data Preparation & Wrangling

- Sales data reflects **monthly percent change** in food & beverage retail sales by state.
- COVID policy datasets were merged to construct:
  - Mask mandate duration
  - Pro-mask enforcement scores
  - Stay-at-home order duration
  - Alcohol and firearm store operational status
- Time was categorized into four periods:
  - **Pre-COVID** (before March 2020)
  - **Panic Phase** (March–December 2020)
  - **Adjustment Phase** (2021)
  - **Post-COVID** (2022 onward)

---

### COVID Sales Impact Analysis

- Sales surged sharply during the Panic Phase, exceeding 10% growth compared to the stable years where average sales growth ~4%, driven by panic buying and stockpiling.
- While sales moderated afterward fast, the Adjustment Phase remained slightly elevated, suggesting consumer behavior did not fully revert to pre-COVID norms.

---

### Policy Impact Analysis

- **OLS Regression** tested linear relationships between policies and sales during the Adjustment Phase
- **Spearman Correlation** captured potential non-linear effects
- **PCA + K-Means clustering** visualized policy styles across states

---

### Seasonal & Regional Analysis

- Used **stable years only (2019, 2022–2024)** to avoid pandemic distortions
- Clustered states by **normalized monthly seasonal patterns**
- Compared **2019 vs. 2024** to identify states that failed to recover seasonal structure

---

### Forecasting

- Built a **seasonal baseline forecast** for Washington State using stable-year averages
- Added **95% confidence intervals**
- Benchmarked against **Facebook Prophet**, evaluated using MAE

---

## Key Findings

### 1. COVID-19 Caused a Structural Sales Shock

![Average Sales by Phase](images/covid_sales_phases.png)

During stable periods, U.S. food and beverage sales grow at roughly **4% month-to-month**.  
However, during the COVID **Panic Phase**, growth surged past **10%**, reflecting panic buying, stockpiling, and sudden shifts in consumption behavior.

Sales moderated afterward but did **not fully revert** to pre-COVID norms during the Adjustment Phase.

---

### 2. State-Level Winners and Losers

![Top vs Bottom States](images/top_bottom_states_heatmap.png)

While most states experienced elevated sales growth during COVID, the magnitude varied:

- **Top performers** (e.g., Wyoming, Montana, Maryland, Washington) saw dramatic spikes
- **Lower performers** (e.g., Hawaii, West Virginia) experienced muted or negative growth

Despite these differences, the majority of states exceeded the stable-year baseline during the pandemic.

---

### 3. COVID Policies Had Minimal Impact on Sales

**OLS Regression Results**
- Very low explanatory power (low R²)
- No statistically significant policy variables (high p-values)

**Spearman Correlation**
- Mask mandates and stay-at-home duration show near-zero correlation with sales
- Alcohol store openings show a weak negative association (~ −0.26)

**Conclusion:**  
Policy differences explain **very little** of the variation in sales outcomes across states.

---

### 4. Policy Clusters Explain Weak Correlations

![Policy PCA Clusters](images/policy_pca_clusters.png)

States grouped into distinct **policy styles**, rather than a single strict–lenient spectrum.  
Most states cluster together despite very different sales outcomes, explaining why neither linear nor non-linear correlations were strong.

---

### 5. Seasonal Consumption Patterns Are Not Regional

![Seasonal Clusters](images/seasonal_clusters.png)

States do share similar seasonal consumption patterns, but these clusters are **geographically mixed**.

No single region dominates a seasonal profile, suggesting that **economic structure and consumer behavior** matter more than geography.

---

### 6. States That Did Not Fully Recover

Seven states showed both:
- Significant shifts in seasonal structure
- Lower average growth in 2024 compared to 2019

These states are spread across regions, indicating uneven recovery not driven by geography alone.

---

### 7. Washington State: Seasonal Baseline Forecast

![WA 6-Month Forecast](images/wa_forecast.png)

Using stable-year seasonality, Washington is projected to experience **steady positive growth** in the first half of 2025, with stronger performance in spring months.

---

### 8. Forecast Uncertainty

![WA Forecast CI](images/wa_forecast_ci.png)

The confidence interval reflects moderate uncertainty but supports a stable, non-volatile outlook for early 2025.

---

### 9. Model Evaluation & Selection

![Prophet Forecast](images/prophet_forecast.png)

| Model | Mean Absolute Error |
|-----|---------------------|
| Seasonal Baseline | **0.91** |
| Prophet | 4.38 |

The Prophet model overfit post-COVID volatility and performed poorly.  
The **simple seasonal baseline** was substantially more accurate and was selected for final forecasting.

---

## How to Run

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels prophet
```

1. Place all CSV files in the project directory
2. Run the notebook top-to-bottom
3. Visualizations render inline

---

## Final Takeaways

COVID created a temporary but extreme demand shock

State policy differences had minimal measurable impact

Seasonal sales behavior is shared across regions

Washington’s retail growth entering 2025 appears stable and predictable
