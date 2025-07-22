<!-- markdownlint-disable MD031 MD033 MD035 MD032 MD004 MD009 MD013 MD045 MD024 MD007 MD023 MD041 -->

## Technical Explanation

<details>
<summary><strong>What We Studied</strong></summary>

- **Main question:** How does solar energy adoption vary across different phases of conflict?  
- **Data source:** IRENA (International Renewable Energy Agency) solar capacity database  
- **Countries analyzed:** Ukraine, Yemen, Sudan, Ethiopia, Libya, Syria, Afghanistan, Iraq, South Sudan  
- **Time frame:** 2000–2024 (varies per country)  
- **Metric:** Installed solar photovoltaic capacity (MW)

#### Conflict Phases

Each country’s timeline was divided into:

1. **Pre-conflict:** Before major violence began  
2. **Active-conflict:** During significant unrest  
3. **Post-conflict:** After hostilities decreased (when applicable)

**Note:** This basic division doesn’t reflect:

- Conflict intensity  
- Geographic extent  
- Transitional or low-intensity periods  

Such simplification may obscure nuances in complex conflicts.

</details>

<details>
<summary><strong>Our Analytical Methods</strong></summary>

### 1. Phase Comparison

**Method:** Averaged solar capacity for each conflict phase  
**Purpose:** Understand which periods saw the most solar development  

**Results:**

- Pre-conflict: 146 MW  
- Active-conflict: 5,724 MW *(skewed by Ukraine)*  
- Post-conflict: 136 MW  

**Note:** Ukraine’s large capacity (8,000+ MW) inflates the active-conflict average.

---

### 2. Country Grouping

**Method:** Classified countries by solar trends across phases  
**Goal:** Highlight national differences in solar development  

**Categories:**

- **Conflict-Fueled Growth:** Increase during conflict (4 countries)  
- **Recovery-Driven Growth:** Surge after conflict (3 countries)  
- **Persistent Low Growth:** Low across all phases (2 countries)  

**Consideration:** Groupings are based on observed patterns but involve some interpretation.

---

### 3. Ukraine Outlier Analysis

**Why:** Ukraine’s solar capacity far exceeds others  
**Impact:**  

- With Ukraine: Active-conflict average = 5,724 MW  
- Without Ukraine: Active-conflict average = 71 MW  

**Justification:** Common practice to handle extreme values separately to preserve clarity.

---

### 4. Linear Regression

**Model:**  
`Solar Growth Rate = Baseline + Conflict Effect + Random Error`  

**Outcome:**  
Conflict periods linked to a +1,359 MW increase  

**Limitations:**  

- Small sample (9 countries)  
- Missing variables (e.g., GDP, aid, policies)  
- Likely statistical violations (non-normal distribution)

---

### 5. Grid vs. Off-Grid Comparison

**Focus:** Differentiated centralized vs. decentralized solar systems  

**Findings:**

- Grid-connected average: 1,600 MW  
- Off-grid average: 50 MW  

**Conclusion:** Even in conflict, centralized infrastructure dominated solar deployment.

---

### **6. Economic Status by Conflict Status**

**Focus:**
Compare average solar capacity across conflict phases by income level (excluding Ukraine).

**Findings:**
- Active-conflict average (low/lower-middle income): ~560–710 MW
- Post-conflict average (upper-middle income): ~150 MW
- Post-conflict average (low income): ~50 MW

**Conclusion:**
During conflict, low and lower-middle income countries had the highest solar growth. Post-conflict trends were uneven across income groups.

--- 
</details>

<details>
<summary><strong>Our Statistical Results</strong></summary>

### Averages (Excluding Ukraine)

- **Pre-conflict:** 0.9 MW  
- **Active-conflict:** 42.5 MW  
- **Post-conflict:** 33.8 MW  

---

### Country-Level Patterns

- **Recovery Growth:** 3 of 6 countries grew post-conflict  
- **Stagnation:** 2 of 6 remained relatively unchanged  
- **Data Gap:** Yemen lacked post-conflict data  

---

### Adoption Timeline

Three waves of expansion:

1. **2004–2010:** Sudan, Ukraine, Afghanistan, Ethiopia  
2. **2015–2018:** Syria, South Sudan  
3. **2018–2025:** Yemen, Iraq  

Many nations saw **500%+ growth** during these periods.

----

### Economic Status

- Peak average: Lower-middle income countries during active conflict (~710 MW).
- Sharp drop for low-income countries post-conflict (~560 ➝ 50 MW).
- Upper-middle income countries show moderate recovery post-conflict.
- Pre-conflict levels are minimal across all groups.

---
</details>

### How Reliable Are Our Results?

#### High Confidence

- Ukraine's outlier status  
- General link between conflict and solar adoption  
- Grid vs. off-grid disparity  

#### Medium Confidence

- Country groupings  
- Post-conflict growth trends  
- Impact estimates  

#### Low Confidence

- Causal interpretations  
- Applicability to other conflict zones  
- Long-term forecasts  

<details>
<summary><strong>Recommendations for Better Analysis</strong></summary>

### With More Resources

1. Add data on foreign aid, economic conditions, and energy policy  
2. Increase temporal resolution (e.g., monthly, quarterly)  
3. Integrate qualitative case studies  
4. Use advanced causal inference methods  

</details>

### Conclusion

Findings are strong within this dataset, but should be interpreted cautiously beyond the included countries.

Our findings reveal distinct patterns in solar development during conflict — especially after adjusting for Ukraine’s outsized influence. Conflict appears correlated with increased solar investment, though causation isn’t confirmed.

We addressed key limitations (e.g., outlier effects), but drawing deeper conclusions requires more granular data and advanced tools.

**Bottom line:**  
Our analysis makes the most of available data. Future research should aim for deeper causal understanding using richer, multi-dimensional datasets.
