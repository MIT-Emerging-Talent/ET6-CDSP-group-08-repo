# Data Exploration

<!-- markdownlint-disable MD031 MD033 MD035 MD032 MD004 MD009 MD013 MD045 MD024 -->

## UN Comtrade data preparation script

### 1. **Input dataset**  

    File:../1_datasets/cleaned_data/UN_comtrade_clean_dataset.xlsx

### 2. Exploratory Data Analysis (EDA) Steps

- Load the cleaned dataset from GitHub.  
- Display general dataset information and description.  
- Generate descriptive statistics for numeric columns:  
   'Mean, standard deviation, minimum, and maximum values'
- Identify potential outliers in relevant columns using simple statistical
   boxplot charts
- Analyze relationships between key variables
- Generate initial visualizations for selected conflict-affected countries
  (e.g., Sudan, Palestine, Ukraine) to highlight trade patterns and potential correlations.

### 3. Key Questions

- Do you have the right data?  
The dataset contains relevant trade information; however, it is not
 comprehensive enough to address all aspects of our research questions.
- Do you need other data?  
Yes, we require additional data on conflict events such as their dates,
intensity, and duration to provide a more complete analysis.
- Do you have the right question?
The research question is well-formulated, but to address it thoroughly, we need
 to collect additional data.
- The research question is well-formulated, but to address it thoroughly, we need
 to collect additional data.

------

## On-Grid Data Preparation

### 1. Input dataset

    File: ../1_datasets/cleaned_data/IRENA_ONGRIDStats.cleaned.xlsx  

### EDA 1

The analysis revealed a substantial gap in electricity capacity between conflict and comparison countries, with conflict-affected regions showing significantly lower infrastructure development.

**Main Discoveries:**
- Conflict areas are getting MORE solar power, not less - went from almost zero to 8,000+ MW in 15 years
- People skip regular electricity and go straight to solar in conflict zones
- Solar growth exploded after 2015 in conflict areas
- Peaceful countries grow solar slowly and steadily

**Surprising Finding:**
War-torn areas are actually adopting solar faster than peaceful ones!

**Overall Insight:** While conflict regions face significant challenges in traditional energy infrastructure, they're experiencing remarkable growth in solar capacity, potentially leapfrogging traditional energy systems.

### EDA 2

Focused only on the 9 conflict countries and phases :  
**Why EDA 2 Focuses on Conflict-Affected Countries?**
- The research question specifically targets **conflict-affected regions.**
- EDA 1 showed _extreme disparities in energy trends_ between conflict and other countries.
- Comparison countries dominate the dataset, making comparisons **statistically unbalanced.**
- Many "comparison" countries did not experience a full-cycle phases periods of conflict in the past 25 years — making classification unclear.
- Conflict countries showed unexpected patterns, like the solar surge in 2015–2020, which deserve deeper investigation individually.
- A focused analysis allows context-specific insights into how conflict influences solar adoption and on-grid and off-grid.

Based on this [**research document**](https://docs.google.com/document/d/1uxgQp8gesLcbfaCGLQAHn3Kgvyu2ZDGxgG-LSWEfq8s/edit?tab=t.0#heading=h.eeoohb5d7fi7) the phases of the 9 conflict countries were added.

**Main Discoveries:**
- **Ukraine has 8,000+ MW** - 30x more than any other country
- **Active Conflict stops solar growth** - capacity drops during wars
- **Three waves**: Early starters (2004-2010), Middle (2015-2018), Recent (2018-2025)
- **Rapid growth possible** - 500%+ increases in stable periods

**Suprising Findings:**
- **War zones still build solar** - Yemen hit 250 MW during conflict
- **2018-2022 was golden period** - most countries started then
- **Recovery is slow** - Sudan/Ethiopia recover best, Libya struggled

**Key Insight:**
- Conflict disrupts but doesn't stop solar development.
  _Countries can rapidly build solar capacity during brief stable periods, but growth becomes highly volatile during wars._

**Numbers:**
- Ukraine: 8,000+ MW
- Yemen: 250 MW  
- Sudan: 100 MW
- Others: Under 50 MW
  
### 2. Exploratory Data Analysis (EDA) Steps

- Load Dataset  
  - Loaded from GitHub using pandas.read_excel() with openpyxl engine.  
- General Information  
  - Used .info() and .describe() to inspect structure, types, nulls, and distributions.
- Descriptive Statistics  
  - Analyzed Electricity Installed Capacity (MW):  
    - Mean: Provided insight into average installed capacity
    - Std deviation: Identified variance across countries and years
    - Min/Max: Helped identify extreme values (potential outliers)
- Missing Values
Checked for nulls using df.isnull().sum() — no major issues found.
- Outlier Detection
  - Used boxplots on:
    - Electricity Installed Capacity (MW) by RE or Non-RE
- Key Variable Relationships
  - Compared capacity trends by:
    - Year vs Classification
    - Producer Type (On-grid/Off-grid) vs Classification
    - Visualized using seaborn lineplot and countplot
- Initial Country Visuals
  - Filtered for conflict-affected countries (e.g., Sudan, Syria, Ukraine)
  - Plotted solar vs other renewables over time
  - Showed variation in growth rates and technology mix across countries

### 3. Key Questions

- **Do you have the right data?**  
 Partially. The dataset provides reliable installed capacity data across countries, years, and technology types, especially for renewable energy trends.
- **Do you need other data?**  
 Yes. To fully understand the role of solar adoption in conflict zones, we needed:
  - Conflict event timelines added
- **Do you have the right question?**
Yes.

-------

## Off-Grid data preparation

### 1. **Input dataset** 

  File:../1_datasets/cleaned_data/IRENA_OFGStats.cleaned.xlsx

### 2. Exploratory Data Analysis (EDA) Steps

- Loaded the clean dataset.
- checked for general information using df.info()
- Made several visuals to understand the gist of the dateset ->
  - Line plots to capture the off-grid capacity and off-grid energy access over time.
  - Bar plots to illustrate Total Off-grid Solar Capacity and Energy access by Region and Conflict Status.
  - Box plots to show Distribution of Off-grid Capacity and Energy access by Conflict Status.
  - bar plots to view the entries by: conflict status and group technology.

### 3. Key Questions

- **Do you have the right data?** 
  - This dataset is highly relevant to our case study, but it need to be accompanied by other data.

- **Do you need other data?**
  - Yes, we need more comprehensive conflict data and a wider array of socioeconomic indicators.
>>>>>>> b132e0758f4669a11ca690bb73cec2d964fc9cef
