# Exploratory Data Analysis of Loan Application Data

## Project Overview
This project involves an in-depth Exploratory Data Analysis (EDA) of loan application data. The primary goal is to identify key patterns, trends, and factors that correlate with a client's likelihood of defaulting on a loan. By understanding these factors, financial institutions can make more informed decisions when assessing loan applications, potentially reducing financial losses due to defaults and ensuring that deserving applicants are not unnecessarily rejected.

## Problem Statement
Banks and financial institutions often face challenges when deciding whether to approve a loan, especially for individuals with limited or no credit history. This decision-making process carries two main types of risks:

1.  **Risk of Business Loss:** If an applicant who is likely to repay the loan is denied, the institution misses out on a potential business opportunity (e.g., interest income).
2.  **Risk of Financial Loss:** If an applicant who is likely to default on the loan is approved, the institution faces a financial loss.

This EDA aims to uncover insights from applicant data to help distinguish between potential defaulters and reliable repayers, thereby assisting in mitigating these risks.

## Dataset
The analysis primarily utilizes two datasets:

1.  `application_data.csv`: Contains detailed information about loan applications and the applicants. This includes socio-demographic data, financial information, and the target variable indicating whether the client defaulted (`TARGET`).
2.  `previous_application.csv`: Contains information about applicants' previous loan applications with other financial institutions.

These datasets are typical for credit risk assessment tasks and allow for a comprehensive analysis of applicant profiles.

## Methodology
The EDA process followed a structured approach:

1.  **Data Loading and Initial Inspection:**
    * Loaded the `application_data.csv` and `previous_application.csv` datasets.
    * Performed initial checks using functions like `.head()`, `.info()`, `.describe()`, and `.shape()` to understand the data structure, data types, and summary statistics.

2.  **Data Cleaning and Preparation:**
    * **Missing Value Treatment:** Identified columns with missing values, analyzed their percentage, and applied appropriate strategies (e.g., dropping columns with a very high percentage of missing 
                                   data, imputation for others where feasible).
    * **Data Type Conversion:** Converted columns to appropriate data types (e.g., `DAYS_BIRTH` to age in years, `DAYS_EMPLOYED` to employment duration in years).
    * **Outlier Handling:** Inspected numerical features for outliers (e.g., `AMT_INCOME_TOTAL`, `AMT_CREDIT`) and considered their impact.
    * **Feature Engineering (Binning):** Binned continuous variables like `AMT_INCOME_TOTAL` into categorical bins (e.g., 'Low', 'Medium', 'High') to facilitate analysis.

3.  **Exploratory Data Analysis:**
    * **Target Variable Analysis:** Examined the distribution of the `TARGET` variable to understand the class imbalance (percentage of defaulters vs. non-defaulters).

     * **Univariate Analysis:**
        * Analyzed the distribution of individual categorical features (e.g., `CODE_GENDER`, `NAME_CONTRACT_TYPE`, `NAME_INCOME_TYPE`, `NAME_EDUCATION_TYPE`, `OCCUPATION_TYPE`) using count plots, often 
          segmented by the `TARGET` variable.
        * Analyzed the distribution of individual numerical features (e.g., `AMT_INCOME_TOTAL`, `AMT_CREDIT`, `AMT_ANNUITY`, client age, employment duration) using histograms and density plots, also 
          segmented by the `TARGET` variable.

    * **Bivariate Analysis:**
        * Investigated relationships between pairs of features, and between individual features and the `TARGET` variable.
        * Used visualizations like stacked bar charts, box plots, and scatter plots (where appropriate).
        * Calculated and visualized a correlation matrix (heatmap) for numerical features to understand linear relationships.

    * **Analysis of Previous Applications:** Performed similar EDA steps on the `previous_application.csv` data and explored ways to merge or relate its insights with the main `application_data.csv`.

## Key Findings and Insights
The EDA revealed several factors that appear to influence loan repayment behavior:

* **Class Imbalance:** A significant imbalance exists, with a much smaller percentage of clients defaulting (around 8% in the `application_data` explored).
* **Income Type:** Certain income types (e.g., 'Businessman', 'Student', 'Pensioner' in some analyses) showed lower or zero default rates compared to others.
* **Education Level:** Applicants with higher education levels (e.g., 'Higher education', 'Academic degree') generally exhibited lower default rates.
* **Occupation Type:** Professionals in roles like 'Core staff', 'High skill tech staff', 'Managers', and 'Accountants' were often found to be more likely to repay loans on time.
* **Age:** Specific age groups (e.g., 60-70 years) showed a lower tendency to default.
* **Gender:** Analysis indicated differences in repayment patterns between genders, with females in some cases showing a higher on-time repayment rate.
* **Contract Type:** 'Revolving loans' were observed to be less risky in some contexts.
* **Family Status & Children:** Marital status (e.g., 'Widow') and the number of children (e.g., no children or a moderate number like 2) showed correlations with repayment behavior.
* **Annuity and Credit Amount:** Higher annuity amounts sometimes correlated with a higher chance of default, while the relationship with total credit amount required careful interpretation.
