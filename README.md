## Covid-19 Impact on Motor Insurance Claim Inflation – Executive Summary

**Author:** Henry Zhang
**Date:** 2023-07-22
[View full report](https://hhappyz88.github.io/GLM-on-motor-insurance-claims/report.html)
### Overview

* Analysed **1.2M policy-months** of motor insurance claims to understand post-Covid claim inflation.
* Objective: Enhance standard GLM models with **macro-economic indicators** to better capture claim cost drivers and inflation trends.

### Key Steps

1. **Data Cleaning & Feature Engineering**
   * Created vehicle age, claim count, and aggregated monthly exposure.
   * Joined macroeconomic data: petrol prices, unemployment, gold, CPI indices, wage index.

2. **Exploratory Analysis**
   * Only **0.5% of policies** have claims; ACT, TAS, NT show very low counts.
   * Newer vehicles slightly more likely to claim; claim cost distributions are highly skewed.
   * Macro variables show weak correlations with claim frequency at aggregated level.

3. **Outlier Handling & Aggregation**
   * ~8% of non-zero claims identified as outliers; retained to preserve tail behaviour.
   * Aggregated by **month, vehicle class, and state** to stabilise low-frequency data.

4. **Modelling Approach**
   * Frequency: **Poisson GLM** (checked for over-dispersion, Negative Binomial optional).
   * Severity: **Gamma GLM with log link**.
   * Exposure included as offset; stepAIC used for variable selection.

5. **Key Findings**
   * **Frequency drivers:** Vehicle age, class, sum insured; macro variables largely insignificant.
   * **Severity drivers:** Petrol price, transport CPI, sum insured; other factors minimal.
   * Extreme claims and rare events are poorly captured due to aggregation and model limitations.

6. **Performance & Limitations**
   * Frequency: RMSE ~1.23 claims/month, Deviance ratio <1 → Poisson assumption reasonable.
   * Severity: Average absolute error ~$16k; Deviance ratio 0.776 → moderate explanatory power.
   * Classical GLMs provide interpretability but underperform on tail events; time-series or transformation-based approaches could improve prediction of rare, high-cost claims.

