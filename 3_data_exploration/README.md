# Data Exploration

<!-- markdownlint-disable MD031 MD033 MD032 MD004 MD009 MD013 MD045 MD024 -->

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

## EDA 1

### 1. Input dataset

    File: ../1_datasets/cleaned_data/IRENA_ONGRIDStats.cleaned.xlsx  

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
    - Year vs Conflict_Status
    - Producer Type (On-grid/Off-grid) vs Conflict_Status
    - Visualized using seaborn lineplot and countplot
- Initial Country Visuals
  - Filtered for conflict-affected countries (e.g., Sudan, Palestine, Ukraine)
  - Plotted solar vs other renewables over time
  - Showed variation in growth rates and technology mix across countries

## EDA 1

The analysis revealed a substantial gap in electricity capacity between conflict and non-conflict countries, with conflict-affected regions showing significantly lower infrastructure development.

**Main Discoveries:**
- Conflict areas are getting MORE solar power, not less - went from almost zero to 8,000+ MW in 15 years
- People skip regular electricity and go straight to solar in conflict zones
- Solar growth exploded after 2015 in conflict areas
- Peaceful countries grow solar slowly and steadily

**Surprising Finding:**
War-torn areas are actually adopting solar faster than peaceful ones!

**Overall Insight:** While conflict regions face significant challenges in traditional energy infrastructure, they're experiencing remarkable growth in solar capacity, potentially leapfrogging traditional energy systems.

## EDA 2

### 3. Key Questions

- **Do you have the right data?**  
 Partially. The dataset provides reliable installed capacity data across countries, years, and technology types, especially for renewable energy trends.
- **Do you need other data?**  
 Yes. To fully understand the role of solar adoption in conflict zones, we need:
  - Conflict event timelines.
- **Do you have the right question?**
Yes.
---

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
