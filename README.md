# Credit Scoring Data Analysis

An exploratory data analysis and preprocessing project focused on **borrowers' risk of defaulting on a loan**. The project examines borrower demographics, employment, income, family characteristics, and loan purpose to explore patterns associated with historical loan repayment behavior.

## Project Overview

The analysis is designed around a bank loan-division use case. The main business questions are:

1. Is there a relationship between having children and repaying a loan on time?
2. Is there a relationship between marital status and loan repayment?
3. Is there a relationship between income level and repayment behavior?
4. How do different loan purposes relate to repayment behavior?

The project demonstrates a complete workflow from raw-data inspection to preprocessing, exploratory analysis, visualization, feature categorization, and business interpretation.

## Dataset

The original dataset contains **21,525 borrower records and 12 variables**.

| Column | Description |
|---|---|
| `children` | Number of children in the family |
| `days_employed` | Total employment experience in days |
| `dob_years` | Customer age in years |
| `education` | Education level |
| `education_id` | Encoded education level |
| `family_status` | Marital/family status |
| `family_status_id` | Encoded family status |
| `gender` | Customer gender |
| `income_type` | Employment/income type |
| `debt` | Historical indicator of failing to repay a loan on time |
| `total_income` | Monthly income |
| `purpose` | Purpose of the loan |

## Analysis Workflow

### 1. Data Loading and Inspection
- Load the CSV dataset with pandas
- Preview rows and columns
- Inspect dataset dimensions
- Review data types
- Generate descriptive statistics
- Examine unique values

### 2. Missing-Value Analysis
- Count missing observations by column
- Calculate missing-value percentages
- Inspect the relationship between missing `days_employed` and `total_income`
- Review missingness across borrower groups
- Remove incomplete rows following the original project workflow

### 3. Data Cleaning
- Inspect invalid and unusual values
- Correct negative values in `children`
- Convert negative employment-day values to absolute values
- Standardize capitalization in `education`
- Convert selected numerical columns to integer type
- Detect and remove duplicated records

### 4. Exploratory Data Analysis
- Summary statistics for numerical variables
- Histograms and distributions
- Boxplots for outlier inspection
- Frequency analysis for categorical variables
- Count plots for borrower characteristics
- Correlation matrix for numerical features

### 5. Feature Categorization
Free-text loan purposes are grouped into broader categories such as:
- Housing
- Vehicle
- Education
- Wedding
- Other

Income is also divided into quantile-based groups to support comparison of repayment behavior across income levels.

### 6. Credit-Risk Analysis
The notebook analyzes default rates across:
- Number of children
- Family status
- Children and family status together
- Education and family status
- Income groups
- Gender
- Income type
- Loan purpose

The analysis uses `groupby`, pivot tables, cross-tabulation, percentages, and visualizations to make the comparisons easier to interpret.

## Key Analytical Questions

### Children and Loan Repayment
Default rates are compared across the number of children in the borrower's family. Group size is retained alongside the percentage so that very small groups can be interpreted carefully.

### Family Status and Loan Repayment
Repayment behavior is compared across marital/family-status categories using both aggregated tables and visualizations.

### Income and Loan Repayment
Borrowers are grouped into income bands, allowing default rates to be compared across low, lower-middle, upper-middle, and high income groups.

### Loan Purpose and Repayment
Loan-purpose text is standardized into broader categories and default rates are calculated for each category.

## Important Interpretation Note

This repository presents **exploratory and descriptive analysis**. Relationships observed in the dataset should not be interpreted as proof that a demographic or financial characteristic causes loan default.

A production credit-scoring system would require additional work such as predictive modeling, train/test validation, fairness assessment, model explainability, and monitoring.

## Technologies and Libraries

- Python
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- Seaborn

## Repository Structure

```text
Credit-Scoring-Data-Analysis/
├── credit_scoring_eng.csv
├── Credit_Scoring_Data_Analysis.ipynb
└── README.md
```

## Skills Demonstrated

- Python programming
- Data cleaning and preprocessing
- Missing-value analysis
- Data-type conversion
- Duplicate detection
- Exploratory Data Analysis (EDA)
- Statistical summaries
- Data visualization
- Feature categorization
- pandas `groupby`
- Pivot tables and cross-tabulation
- Credit-risk data interpretation
- Translating business questions into data analysis

## How to Run

1. Clone or download the repository.
2. Keep `credit_scoring_eng.csv` in the same directory as the notebook.
3. Open `Credit_Scoring_Data_Analysis.ipynb` in Jupyter Notebook, JupyterLab, VS Code, or Google Colab.
4. Install the required packages if necessary:

```bash
pip install pandas numpy matplotlib seaborn
```

5. Run the notebook cells from top to bottom.

## Author

**Samaher Alsharif**  
Data Science | Python | Exploratory Data Analysis
