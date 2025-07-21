# Data Analysis

<!-- markdownlint-disable MD031 MD033 MD035 MD032 MD004 MD009 MD007 MD013 MD045 MD024 MD001 -->
## _Analytical Questions_

## Q1. **What are the trends in solar energy adoption across the conflict cycle—pre-conflict, active conflict, and post-conflict periods—in conflict-affected countries?** 

> **Analysis File:** [phases_analysis.ipynb](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/main/4_data_analysis/phases_analysis.ipynb)  
> **Technical Explanation:** [tech_exp.md](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/9ab2b7b9b55ea2ae81c0e6b93cc95eeace6f59e7/4_data_analysis/phases_analysis/3.tech_exp.md)  
> **Non-Technical Explanation:** [non_tech_exp.md](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/1d6bc8faea79a39dbc9175977e4577ed14e26799/4_data_analysis/phases_analysis/2.non_tech_exp.md)

<details>
<summary><b>1. Dataset</b></summary>

#### A. **Input dataset**  

- **File**: `../1_datasets/cleaned data\ONG_conflictcountriesonly.xlsx`  
- **Description:** Contains annual electricity installed capacity (MW) per the 9 countries only, with corresponding conflict phase classification.

#### B. **Data Quality & Standardization:**  

  - **Missing Data Check:**
    - No missing values were found across all columns, including:
      - Country, Year, Electricity Installed Capacity (MW), and others.
    - A check using `pandas.isnull().sum()` confirmed zero null values per column.
    - No interpolation was necessary.

  - **Data Standardization**
    - **Country column**    
     Cleaned to ensure consistency by:
       - Removing leading/trailing whitespace
       - Converting all names to title case (e.g., "sudan" → "Sudan")

    - **Year column**  
       Ensured to be of integer type to allow accurate sorting and grouping by year.

#### C. **Sorting the Dataset**

To prepare for time-series analysis and ensure accurate visualizations:  
- The dataset was **sorted by `Country` and `Year`** using `pandas.sort_values()`.

This ensures that each country’s solar energy data appears in **chronological order**, which is essential for:
  - **Line plots**
  - **Phase-based comparisons**
  - **Trend analysis over time**

> Sorting prevents jumbled or misleading graphs and allows clear visualization of patterns like solar capacity growth from pre-conflict to post-conflict periods.

</details>

<details>
<summary><b>2. Conducting Analysis</b></summary>

To answer the question the following steps were taken:

**a. Analysis Techniques Used**:  
- **Line Charts**: Solar adoption trends by country over time.
- **Stacked Bar Charts**: Comparison of installed capacity per conflict phase.
- **Heatmaps**: Visual growth intensity per country and year.
- **Regression Plots**: Basic linear regression during conflict periods.
- **Archetype Table**: Pattern classification of country behaviors.  
  
 Charts and visuals generated using `matplotlib`, `seaborn`.  
Output folder for **graphs only:**  `4_data_analysis/phases_analysis/2.output_graphs`

</details>

<details>
<summary><b>3. Assumptions and Limitations</b></summary>

#### - Assumptions

- Conflict phase years manually assigned using conflict timelines.
- Off-grid data may be underreported in national statistics.
- Growth during conflict may be due to emergency policies or donor funding, not sustained planning.

#### - Limitations

- Incomplete post-conflict data for countries like Syria and Yemen, some are even still active.
- Data does not account for:
  - Localized variations in conflict severity
  - Influence of external aid or solar subsidies
- Small dataset (only 9 countries) limits global generalization.
- "Conflict period" definitions may not fully reflect complex realities.
- Installed ≠ working — some reported capacity might not be functional.

</details>

<details>

<summary><b>4. Key Findings & Summary</b></summary>

#### - Conflict-Phase Solar Adoption Summary

| **Conflict Phase**     | **Key Countries**                       | **Observation**                                                           |
|------------------------|-----------------------------------------|---------------------------------------------------------------------------|
| **Pre-Conflict**       | Ethiopia, Sudan                         | Very limited growth — solar was not a strategic priority pre-conflict     |
| **Active-Conflict**    | Ukraine, Yemen, Sudan, Afghanistan      | Peak solar installation, driven by emergency needs and resilience efforts |
| **Post-Conflict**      | Iraq, South Sudan, Afghanistan          | Recovery and growth due to international aid and reconstruction support   |

---

#### - Archetype-Based Country Patterns

| Archetype                | Countries                          | Traits                                                                |
|--------------------------|------------------------------------|-----------------------------------------------------------------------|
| **Conflict-Fueled Growth**     | Ukraine, Yemen, Syria, Sudan       | Rapid adoption during war; survival and independence were key drivers |
| **Recovery-Driven Growth**     | Iraq, South Sudan, Afghanistan     | Modest growth during war, stronger recovery post-conflict             |
| **Stalled Post-Conflict**      | Ukraine (dip), Yemen (plateau)     | Growth halted after early gains                                       |
| **Fragile, Flat Growth**       | Libya, Ethiopia                    | Low growth in all phases                                              |

---
<details>
<summary><b>More analysis</b></summary>

#### - Regression Analysis: Solar Capacity vs. Conflict Period

- **Model Output:**
  - **Coefficient**: +1359.32
  - **Intercept**: 568.99
- **Interpretation:**  
  > On average, solar capacity grew significantly during conflict periods, suggesting a positive correlation. Conflicts can act as a disruptive yet accelerating factor for decentralized energy systems.

#### - On-Grid vs Off-Grid Trends

**1. Grid-Connected Solar Dominates:**
- Avg. grid capacity: ~1,600 MW
- Avg. off-grid: ~50 MW

**2. Off-Grid Systems Used During Conflict:**
- Portable and fast to deploy
- Especially important in rural conflict zones
</details>
</details>

### Takeaway Insights

1. **Conflict as catalyst:** Solar adoption often accelerates during active conflicts out of necessity
2. **Post-conflict uncertainty:** Recovery phases don't guarantee continued growth without proper governance
3. **Archetypal patterns:** Countries follow predictable behavioral patterns useful for forecasting interventions
4. **Grid vs. Off-grid:** Grid-connected systems dominate (~1,600 MW avg) but off-grid crucial during conflicts (~50 MW avg)
