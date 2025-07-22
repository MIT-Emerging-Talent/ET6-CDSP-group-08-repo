# 🧪 Technical Description of Analysis and Results (Updated with Pearson Correlation)

## 1. Objective

This analysis examined whether trends in solar equipment imports align
with trends in solar electricity deployment across four conflict-affected
countries: **Sudan**, **Ukraine**, **Yemen**, and **Ethiopia**. It aimed to
assess how consistently the different data sources reflect real-world solar
adoption patterns, especially in fragile or disrupted energy systems.

---

## 2. Techniques Used

### a. Data Aggregation

The analysis aggregated raw data by `Country` and `Year` using
`.groupby()` and `.sum()` for the key columns: `Imports_USD`, `OnGrid_MW`,
and `OffGrid_MW`. This approach simplified the timeline and made it easier
to compare values across countries and datasets.

### b. Filtering & Cleaning

Non-solar entries were removed, such as those related to hydro and fossil
fuels. The focus was placed on technologies labeled **"Solar PV (Others)"**
and **"Solar photovoltaic"**. This ensured the analysis stayed focused on
solar electricity and maintained consistency across datasets.

### c. Normalization

Min-Max normalization was used to scale values like import dollars and
deployment megawatts between 0 and 1. This allowed for fair visual
comparisons across variables with different units.

### d. Dataset Merging

The datasets were merged using `pd.merge()` on the `Year` column (and
`Country` when needed). This enabled direct year-by-year comparison of
import and deployment data from different sources.

### e. Pearson Correlation Analysis

After merging and normalizing the datasets, **Pearson correlation
coefficients** were calculated between the compared variables (e.g., imports
vs on-grid MW, imports vs off-grid MW). This provided a quantitative measure
of the linear relationship between trends, supplementing the visual
inspection.

### f. Visualization

Line plots were created to compare:

- Imports vs on-grid solar in **Ukraine**
- Imports vs off-grid solar in **Yemen**
- Imports vs off-grid solar in **Ethiopia**
- On-grid vs off-grid solar in **Sudan**

These visualizations helped identify patterns, potential lags, or
misalignments in deployment and import activity.

---

## 3. Country-Specific Results

In **Sudan**, the analysis compared on-grid and off-grid solar deployment.
Off-grid systems appeared to grow more independently from the grid,
suggesting the importance of decentralized solar in fragile contexts.

In **Ukraine**, imports and on-grid solar deployment showed some
alignment, though the Pearson correlation didn't show strong correlation
(0.343), that properly comes from the fact that the On-Grid data set has
some duplicated values, and other possible causes.

In **Ethiopia**, the correlation between imports and off-grid deployment was
strong (0.9), but the time range was only between 2013 and 2023.

In **Yemen**, same case as Ethiopia, with the available data being even more limited.

---

## 4. Possible Flaws in the Analysis

- Import value does not directly equate to installed capacity. Equipment may
be imported but not deployed immediately — or at all. Also, time lags
between import and deployment were not modeled, which could hide real
relationships.
- Several countries lacked full annual coverage across all datasets, limiting
the depth of trend analysis.
- Min-Max normalization can obscure the actual
scale of deployment and imports, making it hard to interpret magnitude
differences.
- While Pearson correlation was applied, it captures only linear
relationships. Nonlinear patterns or delayed effects would not be detected
using this method. Additionally, conflict data was not integrated, which is
a core component of the broader research question.

---

## 5. Alternative Approaches

- Lagged correlation or
regression could reveal whether imports in one year predict deployment in
the next.
- Adding conflict data — such as number of conflict events or fatalities —
would allow for direct correlation with deployment or import behavior.
- Nonlinear modeling techniques or time-series methods could also be used in
more advanced analysis stages.

---

## 6. Libraries Used

- `pandas`: for data manipulation, aggregation, filtering, merging
- `matplotlib.pyplot`: for line and scatter plots
- `seaborn` *(optional)*: useful for enhanced plotting or correlation
  heatmaps
