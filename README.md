# Credit Scoring Data Analysis

A comprehensive **data preprocessing and exploratory data analysis (EDA)** project focused on borrowers' risk of defaulting on a loan. The analysis prepares customer credit data for a bank's loan division and investigates whether borrower characteristics are associated with historical repayment behavior.

## Project Objective

Credit scoring is used to evaluate a potential borrower's ability to repay a loan. This project applies Python-based data analysis to customer demographic, employment, income, family, debt, and loan-purpose information.

The analysis focuses on four main questions:

1. Is there a relationship between having children and repaying a loan on time?
2. Is there a relationship between marital status and loan repayment?
3. Is there a relationship between income level and repayment behavior?
4. How do different loan purposes relate to repayment behavior?

The repository demonstrates the complete analytical workflow from loading raw data through preprocessing, exploration, visualization, feature transformation, and interpretation.

## Dataset Overview

The original dataset contains **21,525 customer records and 12 variables**. Each row represents one customer considered in a credit-scoring analysis.

| Column | Type | Description |
|---|---|---|
| `children` | Numerical | Number of children in the family |
| `days_employed` | Numerical | Number of days employed |
| `dob_years` | Numerical | Customer age in years |
| `education` | Categorical | Customer education level |
| `education_id` | Numerical ID | Education identifier |
| `family_status` | Categorical | Marital/family status |
| `family_status_id` | Numerical ID | Family-status identifier |
| `gender` | Categorical | Customer gender |
| `income_type` | Categorical | Employment/income type |
| `debt` | Binary | Whether the customer has a history of loan debt/default |
| `total_income` | Numerical | Monthly income |
| `purpose` | Categorical/Text | Purpose of the loan application |

## Analysis Workflow

### 1. Environment Setup

The notebook imports the libraries required for data manipulation, text processing, and visualization, including:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `nltk`
- `WordNetLemmatizer`
- `SnowballStemmer`

### 2. Data Loading and Initial Inspection

The dataset is loaded into a pandas DataFrame and inspected using methods such as:

- `head()` to preview customer records
- `shape` to identify dataset dimensions
- `info()` to inspect column types and non-null counts
- `describe()` for descriptive statistics
- `value_counts()` and `unique()` for categorical and discrete-variable exploration

The initial dataset contains **21,525 rows × 12 columns**.

### 3. Missing-Value Analysis

Missing values are investigated before performing the main analysis. The original data contains missing observations in:

| Column | Missing Values |
|---|---:|
| `days_employed` | 2,174 |
| `total_income` | 2,174 |

The notebook examines the missing-data pattern and follows the original project workflow by removing incomplete records before continuing with detailed exploration.

After dropping rows containing missing values, the analysis proceeds with approximately **19.3K complete customer records**.

### 4. Data Quality and Preprocessing

Each variable is inspected for invalid, inconsistent, duplicated, or unusual values.

#### Children

The `children` column is examined using unique values, frequency tables, descriptive statistics, and boxplots. Values include:

`0, 1, 2, 3, 4, 5, -1, 20`

The negative value `-1` is treated as an invalid entry and corrected during preprocessing. Extreme values are also identified for inspection.

#### Employment Duration

`days_employed` is explored through descriptive statistics and distribution analysis. The column contains unusual values and large differences between typical observations and extreme employment-duration records, making outlier inspection an important preprocessing step.

#### Age

`dob_years` is analyzed to understand the customer age distribution and identify unusual values that may require attention.

#### Education

The notebook identifies inconsistent capitalization in education categories, for example variations of the same education level written in uppercase, lowercase, and title case. These inconsistencies are standardized to improve grouping and analysis.

Education identifiers are also explored to understand the encoded categories. The customer base is dominated by **secondary education** records.

#### Family Status

Five family-status groups are represented:

- Married
- Civil partnership
- Unmarried
- Divorced
- Widow / widower

After missing-value removal, `married` is the largest group, with more than **11K records**.

#### Gender

The notebook inspects gender categories and identifies a single unusual `XNA` observation in addition to `F` and `M`. This record is removed because its gender cannot be reliably inferred.

#### Income Type

Employment/income categories are explored, including:

- Employee
- Business/partner
- Retiree
- Civil servant
- Unemployed
- Student
- Entrepreneur
- Maternity/paternity leave

The distribution shows that employees represent the largest customer group.

#### Duplicate Records

The notebook checks duplicated observations and handles them as part of the cleaning process to avoid repeated records affecting the analysis.

## Exploratory Data Analysis

### Numerical Analysis

Numerical variables are explored using:

- Descriptive statistics
- Histograms
- Boxplots
- Distribution plots
- Correlation analysis where appropriate

This helps identify skewness, extreme values, central tendencies, and differences across customer groups.

### Categorical Analysis

Categorical variables are explored using:

- Frequency tables
- `value_counts()`
- Count plots
- Grouped bar charts
- Cross-tabulation
- Pivot tables

These techniques make it easier to compare customer profiles and repayment behavior.

## Credit Risk Analysis

The target variable is `debt`, where the analysis compares the proportion of customers with historical repayment problems across borrower groups.

### Number of Children vs. Debt

The notebook evaluates whether repayment behavior differs according to the number of children in a family. Default/debt rates are calculated for each group and visualized for comparison.

This analysis is descriptive: differences between groups indicate associations in this dataset and do not establish that having children causes default.

### Family Status vs. Debt

Debt rates are compared across marital-status groups to investigate whether repayment patterns differ among married, unmarried, divorced, civil-partnership, and widowed customers.

### Income vs. Debt

`total_income` is explored through summary statistics, histograms, and boxplots. The distribution is right-skewed and contains high-income outliers.

Income-based comparisons are then used to explore whether repayment behavior varies across customer income levels.

### Income Type and Gender

The analysis also compares income patterns across employment categories and gender, providing additional context about the customer population.

### Education and Customer Characteristics

Education levels and their frequencies are analyzed alongside other demographic variables to better understand the composition of the borrower dataset.

## Loan Purpose Analysis

The original `purpose` column contains many different text descriptions for conceptually similar loan purposes. To make the analysis more interpretable, loan descriptions are grouped into broader categories based on keywords.

The analysis considers categories such as:

- **Housing / Real Estate** — house, housing, property, real estate, construction-related purposes
- **Education** — education, university, school, learning, and study
- **Vehicle** — car purchases and related vehicle purposes
- **Wedding** — wedding and marriage expenses
- **Investment / Property-related activities**
- **Renovation / Building-related purposes**
- **Other** — descriptions not captured by the main groups

The categorized purposes are analyzed using frequency counts and visualizations. Housing and real-estate-related requests form a major portion of loan applications in the analyzed data.

## Methods Used in the Notebook

The project demonstrates practical use of pandas and Python techniques such as:

- DataFrame creation and inspection
- Missing-value detection
- Data filtering
- Conditional replacement
- String standardization
- Type conversion
- Duplicate detection
- Descriptive statistics
- `groupby()` aggregation
- `pivot_table()`
- `crosstab()`
- Custom categorization functions
- Lambda expressions
- Frequency and percentage calculations
- Data visualization
- Outlier inspection

## Visualizations

The notebook includes visual analysis using Matplotlib and Seaborn, including:

- Histograms
- Boxplots
- Count plots
- Bar plots
- Grouped comparisons
- Distribution visualizations

The saved notebook contains its executed outputs, allowing the analysis and results to be viewed directly on GitHub without rerunning every cell.

## Key Findings

The exploratory analysis highlights several patterns in the customer data:

- The dataset contains missing values specifically in `days_employed` and `total_income`, requiring preprocessing before analysis.
- Several columns contain data-quality issues such as inconsistent capitalization and unusual numerical values.
- Secondary education is the most common education level among customers.
- Married customers form the largest family-status group.
- Employees form the largest employment/income-type group.
- Total income has a skewed distribution with high-value outliers.
- Repayment behavior varies across borrower groups such as number of children, family status, income, and loan purpose.
- Loan-purpose descriptions can be transformed into broader business categories to make repayment comparisons more interpretable.
- Housing and real-estate-related purposes are among the most common reasons for loan applications in the dataset.

## Important Interpretation Note

This project is an **exploratory and descriptive analysis**. Observed differences between customer groups should not be interpreted as proof that demographic or financial characteristics cause loan default.

A production credit-scoring solution would require additional stages such as predictive modeling, train/validation/test evaluation, fairness assessment, explainability, model monitoring, and appropriate governance before deployment.

## Technologies

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- NLTK
- Jupyter Notebook / Google Colab

## Repository Structure

```text
Credit-Scoring-Data-Analysis/
├── credit_scoring_eng.csv
├── credit_scoring_eng.ipynb
└── README.md
```

### `credit_scoring_eng.csv`
Raw customer credit-scoring dataset used throughout the analysis.

### `credit_scoring_eng.ipynb`
Complete analysis notebook containing data preprocessing, exploratory analysis, visualizations, analytical questions, conclusions, and executed outputs.

### `README.md`
Detailed project documentation and summary of the analytical workflow.

## Skills Demonstrated

- Python programming
- Data preprocessing
- Data cleaning
- Missing-value analysis
- Data-quality assessment
- Exploratory Data Analysis (EDA)
- Categorical-data analysis
- Numerical-data analysis
- Outlier detection
- Text/category preprocessing
- Feature categorization
- Data visualization
- pandas `groupby`
- Pivot tables
- Cross-tabulation
- Business-oriented data interpretation
- Credit-risk exploratory analysis
- Translating business questions into analytical tasks

## How to Run

1. Clone or download this repository.
2. Keep `credit_scoring_eng.csv` in the same directory as the notebook.
3. Open `credit_scoring_eng.ipynb` using Jupyter Notebook, JupyterLab, VS Code, or Google Colab.
4. Install the required packages if necessary:

```bash
pip install pandas numpy matplotlib seaborn nltk
```

5. Run the notebook cells sequentially from top to bottom.

## Author

**Samaher Alsharif**  
Data Science | Python | Exploratory Data Analysis