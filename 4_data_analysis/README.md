# Data Analysis

<!-- markdownlint-disable MD031 MD033 MD035 MD032 MD004 MD009 MD007 MD013 MD045 MD024 -->
## _Analytical Questions_

## Q1. **What are the trends in solar energy adoption across the conflict cycle—pre-conflict, active conflict, and post-conflict periods—in conflict-affected countries?** 

>[phases analysis.ipynb](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/main/4_data_analysis/phases_analysis.ipynb)

## 1. **Dataset**  

### A. **Input dataset**  

- **File**: `../1_datasets/cleaned data\ONG_conflictcountriesonly.xlsx`  
- **Description:** Contains annual electricity installed capacity (MW) per the 9 countries only, with corresponding conflict phase classification.

### B. **Data Quality & Standardization:**  

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

### C. **Sorting the Dataset**

To prepare for time-series analysis and ensure accurate visualizations:

- The dataset was **sorted by `Country` and `Year`** using `pandas.sort_values()`.
- This ensures that each country’s solar energy data appears in **chronological order**, which is essential for:
  - **Line plots**
  - **Phase-based comparisons**
  - **Trend analysis over time**

> Sorting prevents jumbled or misleading graphs and allows clear visualization of patterns like solar capacity growth from pre-conflict to post-conflict periods.

### 2. **Conducting Analysis**

To answer the question the following steps were taken:

**a. Analysis Techniques Used**:  
- **Line Charts**: Solar adoption trends by country over time.
- **Stacked Bar Charts**: Comparison of installed capacity per conflict phase.
- **Heatmaps**: Visual growth intensity per country and year.
- **Regression Plots**: Basic linear regression during conflict periods.
- **Archetype Table**: Pattern classification of country behaviors.

 Charts and visuals generated using `matplotlib`, `seaborn`.

Output folder:  
`4_data_analysis/phases_analysis/2.output_graphs`

### 3. Assumptions & Limitations

#### Assumptions

- Conflict phase years manually assigned using conflict timelines.
- Off-grid data may be underreported in national statistics.
- Growth during conflict may be due to emergency policies or donor funding, not sustained planning.

#### Limitations

- Incomplete post-conflict data for countries like Syria and Yemen.
- Data does not account for:
  - Localized variations in conflict severity
  - Influence of external aid or solar subsidies
- Ukraine’s extreme growth (50,000+ MW) skews comparative visuals.

### 4. Key Findings & Summary

#### Conflict-Phase Solar Adoption Summary

| **Conflict Phase**     | **Key Countries**                       | **Observation**                                                           |
|------------------------|-----------------------------------------|---------------------------------------------------------------------------|
| **Pre-Conflict**       | Ethiopia, Sudan                         | Very limited growth — solar was not a strategic priority pre-conflict     |
| **Active-Conflict**    | Ukraine, Yemen, Sudan, Afghanistan      | Peak solar installation, driven by emergency needs and resilience efforts |
| **Post-Conflict**      | Iraq, South Sudan, Afghanistan          | Recovery and growth due to international aid and reconstruction support   |

---

#### Archetype-Based Country Patterns

| Archetype                | Countries                          | Traits                                                                |
|--------------------------|------------------------------------|-----------------------------------------------------------------------|
| **Conflict-Fueled Growth**     | Ukraine, Yemen, Syria, Sudan       | Rapid adoption during war; survival and independence were key drivers |
| **Recovery-Driven Growth**     | Iraq, South Sudan, Afghanistan     | Modest growth during war, stronger recovery post-conflict             |
| **Stalled Post-Conflict**      | Ukraine (dip), Yemen (plateau)     | Growth halted after early gains                                       |
| **Fragile, Flat Growth**       | Libya, Ethiopia                    | Low growth in all phases                                              |

---

#### Phase-Based Summary Table

| Country        | Pre-Conflict (MW) | Active-Conflict (MW) | Post-Conflict (MW) | Trend        |
|----------------|-------------------|------------------------|---------------------|--------------|
| **Ukraine**     | 1,310.7           | 48,770.4               | 0.0                 | Surge → Stalled |
| **Yemen**       | 2.4               | 2,236.0                | 0.0                 | Surge → Stalled |
| **Sudan**       | 0.01              | 713.5                  | 0.0                 | Surge → No data |
| **Afghanistan** | 0.0               | 292.0                  | 160.4               | Growth → Recovery |
| **Iraq**        | 0.0               | 175.5                  | 273.0               | Recovery        |
| **South Sudan** | 0.0               | 9.9                    | 53.4                | Recovery        |
| **Ethiopia**    | 75.1              | 62.6                   | 42.7                | Decline        |
| **Libya**       | 15.6              | 39.3                   | 29.3                | Weak growth     |
| **Syria**       | 0.0               | 228.5                  | 0.0                 | Conflict-only   |

---

#### Regression Analysis: Solar Capacity vs. Conflict Period

- **Model Output:**
  - **Coefficient**: +1359.32
  - **Intercept**: 568.99
- **Interpretation:**  
  > On average, solar capacity grew significantly during conflict periods, suggesting a positive correlation. Conflicts can act as a disruptive yet accelerating factor for decentralized energy systems.

---

#### On-Grid vs Off-Grid Trends

**1. Grid-Connected Solar Dominates:**
- Avg. grid capacity: ~1,600 MW
- Avg. off-grid: ~50 MW

**2. Off-Grid Systems Used During Conflict:**
- Portable and fast to deploy
- Especially important in rural conflict zones

---

#### Takeaway Insights

- Solar capacity **grew most during active conflicts**, often out of necessity.
- Post-conflict periods do not guarantee growth — **recovery requires governance, aid, and sustained planning**.
- **Ukraine’s case is exceptional**, with +4644% growth during war.
- **Countries behave in archetypal patterns** — useful for forecasting or designing interventions.

---

## 📎 Visual Summary Examples

Include 2–4 key charts in your README (with captions like):

```markdown
![Solar Adoption by Conflict Phase](./path/to/image.png)
> Chart showing how solar capacity surged during active conflict in Ukraine and Yemen.
