# Data Preparation

<!-- markdownlint-disable MD031 MD033 MD035 MD032 MD004 MD009 MD013 MD045 MD024 MD007 MD029 -->
## On-Grid Data Preparation Script

This script processes the **on-grid electricity data** from the IRENA dataset.

### Input

- **File**: [IRENA_Stats_extract_2025_H1_raw.xlsx](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/main/1_datasets/raw_data/IRENA_Stats_extract_2025_H1_raw.xlsx)
  - **Sheet**: `Country`
  - **Path**: `1_datasets/raw_data/`

### Process

- Added `Classification` column by filtering conflict-affected countries.
- Fills missing values in key columns
- Filtered out years according to project scope (2010 - 2024)
- Drops unused column `M49 code`

#### **Selected Conflict-Affected Countries**

Nine countries were chosen based on having experienced pre-conflict, active conflict, and in some cases post-conflict phases within the past 25 years:  
 **Syria, Iraq, Sudan, South Sudan, Ethiopia, Ukraine, Yemen, Libya, Afghanistan**

Country Classification:  
- **"Conflict Countries"**: Countries that experienced identifiable pre-conflict phases (all 9 selected countries: Syria, Iraq, Sudan, South Sudan, Ethiopia, Ukraine, Yemen, Libya, Afghanistan)
- **"Comparison Countries"**: Additional countries with mixed conflict/non-conflict status that did not experience pre-conflict phases, included for comparative analysis

Key Selection Criteria:  
- Time frame: Past 25 years
- Must include pre-conflict phase (primary distinguishing factor) to see the solar adoption increases or decreases when active conflict.
- Represent different stages of conflict progression (pre-conflict → active conflict → post-conflict where applicable)

### Output

1. **File**: `IRENA_ONGRIDStats.cleaned.xlsx`
  - **Sheet**: `Cleaned_OnGrid_Data`
  - **Path**: `1_datasets/cleaned_data/`
  - **File Link**: [IRENA_ONGRIDStats.cleaned.xlsx](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/main/1_datasets/cleaned_data/IRENA_ONGRIDStats.cleaned.xlsx)

---

## UN Comtrade data preparation script

1. **Input dataset**  
   - **File**: `../1_datasets/raw_data/UN_Comtrade_imports_dataset_raw.xlsx`  
   - **Loaded as**: `raw_df` (and copied to `df`)

2. **Processing steps**  
   - **Drop unneeded columns**: Drop unneeded columns: a long list of technical
  fields (e.g. frequency codes, partner metadata, alternative quantity fields,
   legacy flags, etc.) is removed in one go.
   - **Rename columns**:

     | original       | new name               |
     | -------------- | ---------------------- |
     | `refYear`      | `Year`                 |
     | `\tISO_Code`   | `Country_Code`         |
     | `reporterDesc` | `Country`              |
     | `cmdCode`      | `Product_Code`         |
     | `cmdDesc`      | `Product_Description`  |
     | `netWgt`       | `Net_Weight_kg`        |
     | `primaryValue` | `Value_USD`            |

   - **Handle missing values**: fill missing `Net_Weight_kg`
    entries with the column mean.  
   - **Inspect**: prints `.shape`, `.info()`, `.isna().sum()`,
    duplicate counts, and random samples to verify cleaning.

3. **Output dataset**  

- **Cleaned data** written to Excel at:  

`../1_datasets/cleaned_data/UN_comtrade_clean_dataset.xlsx`

- No other files are created or saved under `/1_datasets`.

---

### Off-Grid data preparation script

1. **Input dataset**
    - **File**: ["IRENA_OFGStats.raw"](https://github.com/MIT-Emerging-Talent/ET6-CDSP-group-08-repo/blob/main/1_datasets/raw_data/IRENA_OFGStats.raw.xlsx)
    - **Sheet**: `data`
    - **Path**: `1_datasets/raw_data/`

2. **Process**

    - Dropped irrelevant columns.
    - Inspected the data to the its shape and whether it has null values or not.
    - Filled the null values.
    - Added a conflict status column.
    - removed any row with `Bioenergy` technology in it.
    - Noticed that there are different units for the value columns, which are
    `1000 m3, thousands, MW`, the 1000 m3 unit was primarily used for bioenergy
    group technology which is irrelevant to our study so I just deleted any
    observation that its group technology is Bioenergy. Regarding the other unit
    which is `thousands`; it mainly measure the number of people using/utilizing
    that technology and `mw` is the unit of the power produced by a technology
    so I had to seperate the dataset into two different ones according to the unit.

3. **Output datasets**

- **File**: `IRENA_OFGStats_mw.cleaned.xlsx`
  - **Sheet**: `Cleaned_Data`
  - **Path**: `1_datasets/cleaned_data/`
- **File**: `IRENA_OFGStats_thousands.cleaned.xlsx`
  - **Sheet**: `Cleaned_Data`
  - **Path**: `1_datasets/cleaned_data/`
