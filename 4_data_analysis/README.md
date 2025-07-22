
# **conflict duration analysis:**

## _Analytical Questions_

**Q1. How does prolonged conflict impact solar product imports and their**
**market dynamics across conflict-affected countries?**

> **Objective:**  
> Explore the relationship between conflict duration and solar product import
 trends, including product category mix and pricing, while comparing
  conflict-affected countries with stable countries.

**Analysis File:**[4_data_analysis\duration_analysis\conflict_duration_analysis.ipynb](duration_analysis/conflict_duration_analysis.ipynb)

Technical Explanation: [4_data_analysis/duration_analysis/technical_explanation.md](duration_analysis/technical_explanation.md)

Non-Technical Explanation: [non_tech_exp.md](duration_analysis/non_tech_exp.md)

### A. Input dataset

- **File:** 4_data_analysis\Conflict_Duration_Analysis\conflict_duration_analysis.ipynb
- **Description:** Annual solar product import data across multiple countries
 (conflict-affected and stable), containing:
  - Country  
  - Year  
  - Product Description  
  - Net Weight (kg)  
  - Import Value (USD)

### B. **Data Processing & Standardization:**  

### Conflict Duration Categories

- **Continuous Conflict Countries:**  
  Afghanistan, Syria, Yemen, Sudan , State of Palestine, Libya, Mali

- **Periodical Conflict Countries:**  
  Iraq, Nigeria, Central African Republic, Ethiopia, Ukraine, Myanmar,
   Pakistan, Mozambique

- **No Conflict Countries:**  
  Germany, Morocco, Rwanda, Saudi Arabia

- **Product Categorization:**  
  Imported solar products classified into:
  - PV Modules  
  - Inverters  
  - Lead-Acid Batteries  
  - Lithium Batteries  
  - Solar Lamps  
  - Solar Generators  
  - Other

**Data Cleaning:**  

- Country names and years standardized.  
- Treating null and zero values.  
- Added new columns to define conflict year status and GDP category.

## The following analyses were conducted

- **Comparison of Solar Imports Over Time:**  
  Total import values compared between:  
  - Continuous Conflict countries  
  - Periodical Conflict countries
  - Stable countries  

- **Product Mix Analysis:**  
  Breakdown of solar product categories imported during conflict group

- **Country-Specific Trends:**  
  Time series of imports by key product categories (PV Modules, Solar Lamps,
   Lithium Batteries) for each group

- **Price Trends:**  
  Analysis of average price per kg for main product categories during conflict
   years to detect market pricing shifts.

Visualizations generated using `matplotlib` and `seaborn`, including line plots,
 bar charts, and shaded conflict period areas.

### Assumptions and Limitations

- Conflict periods are defined based on available historical data but may
   not fully capture localized, intermittent, or unreported violence within
    countries.  
- Import data represents officially recorded legal trade and may omit
 informal, unreported, or smuggled goods, especially common in conflict zones.  
- Product categorization relies on keyword matching in product descriptions,
   which may lead to misclassification or omission of some items.  
- Some import data is missing for key conflict periods in certain
  countries—for example, Syria after 2011 and Sudan after 2018—potentially
   biasing trend analyses
 for these regions.  
- Stable countries were selected as regional comparators; however, they differ
   in socio-economic and political contexts, which may influence import trends
   independently of conflict status.

### Key Findings & Summary**Import Value Trends:**  

- Imports spike during conflict years in many conflict-affected countries.  
- Conflict-period imports exceed pre/post-conflict periods for several
 countries.
- Stable countries show steadier, slower growth in imports.

**Product Mix Differences:**  

- PV Modules dominate imports in both conflict and stable countries.  
- During conflicts, Solar Lamps and Lithium Batteries have a larger share,
 reflecting urgent needs for portable power.  
- Lead-Acid Batteries and Inverters maintain smaller shares overall.

**Country Case Studies:**  

- Syria and Yemen show notable import surges during conflict, especially for
   portable products.  
- Ukraine displays sustained import growth throughout conflict periods.

### Takeaway Insights

1. **Conflict periods often coincide with increased solar imports in affected
 countries, likely due to humanitarian aid and urgent energy needs.**  
2. **Product mixes shift towards portable and off-grid solutions (solar lamps,
 lithium batteries) during conflicts, emphasizing resilience needs.**  
3. **Stable countries exhibit steadier import growth, indicating planned,
 long-term solar adoption rather than reactive demand.**  
4. **Price fluctuations during conflict highlight supply chain vulnerability
 but also market adaptation to urgent demand.**  
5. **Country-specific trends reveal how the nature and duration of conflicts
 shape solar product import patterns, useful for targeting aid and development programs.**
