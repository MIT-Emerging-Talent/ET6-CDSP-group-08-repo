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
- Added Economic Status column to help in analysis.
  
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
- Ukraine’s extreme growth (50,000+ MW) skews comparative visuals.

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

## Q2. **To what extent are these datasets comparable, and what differences, if any, exist in what they measure?** 

> **Analysis File:** [comparison_analysis.ipynb](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/comparison-analysis/4_data_analysis/data_comparison_analysis/comparison_analysis.ipynb)  
> **Technical Explanation:** [tech_exp.md](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/comparison-analysis/4_data_analysis/data_comparison_analysis/tech_explanation.md)  
> **Non-Technical Explanation:** [non_tech_exp.md](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/comparison-analysis/4_data_analysis/data_comparison_analysis/non_tech_explanation.md)

<details>
<summary><b>1. Dataset</b></summary>

#### A. **Input dataset**  

We used three datasets to analyze solar adoption trends across four conflict-affected countries:

- **UN Comtrade**: Annual solar equipment import values (USD).
- **IRENA**: On-grid solar capacity (MW), by year and country.
- **IRENA**: Off-grid solar capacity (MW), by year and country.

The countries examined were:

- **Ukraine** (imports vs on-grid),
- **Sudan** (on-grid vs off-grid),
- **Yemen** and **Ethiopia** (imports vs off-grid).

All datasets were filtered to include only solar technologies (e.g., _“Solar photovoltaic”_), and aggregated by year and country.

</details>

<details>
<summary><strong>2. Conducting Analysis</strong></summary>

### Steps Taken

- **Cleaning & Filtering**: Removed non-solar entries, retained only relevant categories like _“Solar PV (Others)”_.
- **Aggregation**: Used `.groupby()` and `.sum()` to calculate total imports and capacity per year.
- **Normalization**: Applied Min-Max scaling to compare variables with different units (USD vs MW).
- **Merging**: Joined datasets on `Year` and `Country` using `pd.merge()` for aligned year-over-year comparison.
- **Correlation**: Calculated Pearson correlation coefficients to quantify linear relationships between variables.
- **Visualization**: Created time-series line and scatter plots for each country and variable pair.

</details>

<details>
<summary><strong>3. Assumptions and Limitations</strong></summary>

### Assumptions

- Import values are assumed to reflect solar-related purchases.
- Conflict data was not yet incorporated, despite being core to the broader research focus.
- On-grid and off-grid systems are considered functionally separate in fragile contexts.
- Min-Max normalization was used to enable direct trend comparisons.

### Limitations

- **Import ≠ Deployment**: Equipment might be stockpiled, unused, or re-exported.
- **No time lags modeled**: Imports may impact deployment in future years.
- **Normalization hides magnitude**: Actual deployment scale is flattened.
- **Sparse data**: Yemen and Ethiopia had limited off-grid data years.
- **Linear focus**: Pearson correlation doesn’t detect nonlinear or delayed effects.
- **Data gaps**: Not all countries had data across all years.
- **Conflict timelines missing**: Deployment may correlate with conflict intensity or aid, but this was not tested.

</details>

<details>
<summary><strong>4. Key Findings & Summary</strong></summary>

- **Ukraine**: Some alignment between import and on-grid deployment trends. Pearson correlation = **0.34**. Visual patterns suggest policy or donor-driven surges.
- **Ethiopia**: Strong correlation (**0.9**) between imports and off-grid deployment (2013–2023), though data range is short.
- **Yemen**: Similar to Ethiopia but even more limited data coverage.
- **Sudan**: On-grid and off-grid deployments grew independently. Off-grid systems surged, possibly due to decentralized aid and resilience strategies.

> **Conclusion**: Import trends sometimes reflect deployment trends — but **not reliably across all contexts**. Aid flows, informal markets, and conflict dynamics complicate the relationship.

</details>
