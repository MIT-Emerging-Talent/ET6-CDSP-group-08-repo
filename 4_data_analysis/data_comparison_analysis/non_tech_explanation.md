# 🔍 Research Conclusions

Our analysis suggests that there is **moderate alignment** between solar
equipment import trends and solar electricity deployment trends in some
conflict-affected countries — notably Ukraine. In contrast, in places like
Sudan, off-grid deployment seems to grow independently from centralized
systems, highlighting the role of solar as a decentralized resilience
technology. However, inconsistencies, missing data, and differing
deployment patterns suggest that **import value alone is not a reliable
proxy** for solar adoption in all contexts.

---

## 📊 Summary of Analysis Approach

We analyzed three datasets:

1. UN Comtrade data on **solar equipment imports** by country and year.
2. IRENA data on **on-grid solar electricity deployment** (MW).
3. IRENA data on **off-grid solar deployment** (MW).

We cleaned and filtered the data to focus only on solar technologies and
aggregated them by year and country. The datasets were then normalized
using Min-Max scaling and merged by year to allow direct comparisons.

We focused on four countries:

- **Ukraine**: imports vs on-grid solar deployment.
- **Yemen** and **Ethiopia**: imports vs off-grid deployment.
- **Sudan**: comparison between on-grid and off-grid deployment only.

For each country, we produced visual plots comparing trends and calculated
**Pearson correlation coefficients** to quantify relationships between
variables.

---

## 📈 Confidence in Results

We have **moderate confidence** in the visual and statistical patterns
observed, especially for countries like Ukraine where data coverage is
relatively complete. The use of Pearson correlation adds robustness to the
findings by quantitatively evaluating trend alignment.

However, confidence is lower in countries with:

- Missing or sparse data (e.g., Yemen)
- Ambiguous reporting structures
- Untracked deployment (e.g., informal solar usage)

---

## ⚠️ Limitations

1. **Imports do not equal usage**: Imported equipment may be unused,
   stockpiled, or exported again.
2. **No modeling of time lags**: Equipment imports may precede deployment
   by 1–2 years — our analysis compares only same-year values.
3. **Normalization hides magnitudes**: Min-Max scaling distorts actual
   values, masking real-world scale differences.
4. **Conflict data not integrated yet**: Despite the conflict-focused
   research question, the current analysis does not yet incorporate
   conflict timelines, severity, or displacement data.
5. **Pearson correlation only captures linear relationships**: Nonlinear or
   lagged relationships remain unexplored.

---

## 🔬 Future Research Directions

1. **Integrate conflict data**: Include metrics like conflict severity,
   number of incidents, or displacement figures to test impact on energy
   access.
2. **Use lagged correlation/regression**: Investigate whether imports in
   one year influence solar deployment in subsequent years.
3. **Model non-linear relationships**: Use more advanced machine learning
   models (e.g., Random Forest, XGBoost) for richer pattern detection.
4. **Compare informal vs formal solar usage**: Especially relevant in
   off-grid contexts like Yemen and Ethiopia.
5. **Spatial analysis**: Match solar deployment to sub-national conflict
   zones to study localized effects.

---

## 🛠️ Techniques & Libraries Used

### Analysis Techniques

- Data cleaning and filtering by energy type
- Grouping and aggregation using `.groupby()`
- Normalization using Min-Max scaling
- Merging datasets by year and country
- Pearson correlation analysis for linear trend alignment
- Time-series line and scatter plots
