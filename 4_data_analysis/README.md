# Data Analysis

<!-- markdownlint-disable MD031 MD033 MD035 MD032 MD004 MD009 MD007 MD013 MD045 MD024 -->
## Analytical Questions

### Q1. **What are the trends in solar energy adoption across the conflict cycle—pre-conflict, active conflict, and post-conflict periods—in conflict-affected countries?**

### 1. **Dataset**  

A. **Input dataset**  
- **File**: `../1_datasets/cleaned data\ONG_conflictcountriesonly.xlsx`  
- **Description:** Contains annual electricity installed capacity (MW) per the 9 countries only, with corresponding conflict phase classification.

B. **Data Quality & Standardization:**  

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

C. **Sorting the Dataset**

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
- Line charts were used to show changes in solar capacity over time for each country.
- Stacked bar charts compared the total installed capacity in each conflict phase (pre, active, post).
- Heatmaps visualized growth rates and intensity across countries and years.

b. **Visualizations**

* All charts were generated using Python (`matplotlib` and `seaborn`).
* Figures include:

  * Country-specific trend lines
  * Grouped bar plots comparing conflict phases
  * A heatmap of yearly growth patterns across countries
* Visuals were exported and saved in the `3_outputs/figures/` folder.

c. **Assumptions & Limitations**

* **Assumptions**:

  * Conflict years were defined manually and may not reflect local or regional variations.
  * Linear interpolation was used in earlier stages, but final dataset had no missing values.
  * Off-grid data may be underestimated in some countries due to underreporting.

* **Limitations**:

  * Some countries had limited or short post-conflict periods (e.g., Syria), which makes comparison uneven.
  * Data does not account for international aid or policy differences which might influence solar growth.
