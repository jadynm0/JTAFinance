# JTAFinance

### SDSS Datathon 2026 -- Personal Finance Case

------------------------------------------------------------------------

## Project Summary

Financial stability looks different across life stages. A 24-year-old
renter with student debt faces very different pressures than a
45-year-old homeowner with dependents.

This project uses **Survey of Financial Security (SFS) microdata** to:

1.  Define a measurable **Financial Risk / Resilience Index**
2.  Build a **validated predictive model**
3.  Simulate **economic shocks**
4.  Segment households into **financial personas**
5.  Provide **data-driven policy recommendations**

The goal - This project research question:

- Among Canadians aged 18–54, which groups are financially vulnerable ?
- What financial characteristics explain vulnerability among Canadians aged 18–54 ?
- How is that vulnerability affected by income and cost-of-living shocks ?

Dataset source: Survey of Financial Security (SFS), Statistics Canada.
Pre-processed subset included in repository.

------------------------------------------------------------------------
# Repository Structure

    JTAFinance/
    │
    ├── Datathon-Personal-Finance.ipynb
    ├── personal_finance_dataset.xlsx
    ├── README.md
    └── requierment.txt

You only need the notebook and dataset to run the project.

------------------------------------------------------------------------
# Setup Instructions (Mac / Windows / Linux)

## 1. Clone or Download

``` bash
git clone <your_repo_url>
cd JTAFinance
```

Or download the ZIP and open the folder.


## 2. Create Virtual Environment

### Mac/Linux

``` bash
python3 -m venv .venv
source .venv/bin/activate
```

### Windows (PowerShell)

``` powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```


## 3. Install Required Packages

``` bash
python -m pip install --upgrade pip
python -m pip install numpy pandas matplotlib seaborn scikit-learn openpyxl
```

Required libraries: - numpy - pandas - matplotlib - seaborn -
scikit-learn - openpyxl (for Excel reading)

------------------------------------------------------------------------
# How to Run the Project

## Option A - VS Code (Recommended)

1.  Open folder in VS Code
2.  Install extensions if prompted:
    -   Python
    -   Jupyter
3.  Open `Datathon-Personal-Finance.ipynb`
4.  Select kernel: `.venv (Python 3.x)`
5.  Click **Run All**


## Option B - Jupyter Notebook

``` bash
python -m pip install jupyter
jupyter notebook
```

Open the notebook and run all cells top to bottom.

------------------------------------------------------------------------
#  Methodology: What the Notebook Does

## 1.Data Cleaning & Renaming

Transforms coded SFS column names into readable labels.

## 2. Feature Engineering

Creates:

-   **Total_Liquidity**
-   **Annual_Expenses_Base**
-   **Years_of_Runway**
-   **Housing_Burden_Ratio**
-   **DTI_Ratio**
-   **Liquidity_Months**
-   **Is_At_Risk_Base** (target variable)

### Financial Risk Definition

A household is classified as **At Risk** if:

-   < 3 months liquidity runway, or
-   Housing burden \> 30%, or 
-   Debt-to-income \> 50%, or
-   Skipped payments, or

## 3. Predictive Modeling

Model: **Random Forest Classifier**

Validation: 
- Train/Test split 
- ROC-AUC 
- F1 Score 
- Confusion Matrix

Interpretability: 
- Random Forest Feature Importance 
- Permutation Importance

## 4. Stress Testing
Simulates adverse economic scenarios to measure how financial vulnerability increases under shock conditions.

Simulates multiple economic shocks:

- Expense inflation (0–30%)

- Income reduction (0–30%)

- Mortgage cost increase

- Rent increase

Outputs:

- At-risk rate vs shock curve

- Newly vulnerable share

- Age group breakdown

- Shock sensitivity (risk increase per 1% shock)


## 5. Financial Personas (Segmentation)

Uses KMeans clustering on:

-   Liquidity Months
-   Housing Burden
-   DTI Ratio
-   Income
-   Total Liquidity

Produces: 
- 5 distinct financial personas 
- Risk % per persona 
- Visual summary

------------------------------------------------------------------------

# Modeling Assumptions & Threshold Justification
To ensure interpretability and policy relevance, the following thresholds were used:

1. Housing burden > 30%

Based on the widely used 30% housing affordability benchmark from Canada Mortgage and Housing Corporation (CMHC) and Statistics Canada.
We assume here that A housing cost burden exceeding 30% of gross household income is an indicators of financial constraint

2. Debt-to-income > 50%

A debt-to-income ratio above 50% was classified as high financial strain
This threshold reflects elevated risk levels relative to Canadian mortgage qualification standards, where total debt service ratios above approximately 44% are considered high by financial regulators such as OSFI.

3. Financial runway < 3 months

Runway < 3 months = insufficient buffer
Canadian financial literacy guidelines commonly recommend 3–6 months of expenses as emergency savings.

4. Annual expenses approximated as 60% of after-tax income

Annual Expenses ≈ 60% of After-Tax Income
There is no official “60% rule,”  but Statistics Canada indicates that housing and utility costs commonly represent 30–50% of household income, and clothing generally represents less than 10% of total household spending
So we take 60% for the assumption 

5. Mortgage interest = 4%

Morgage interst is vary acorss banks and buyer, and accoriding to the most recent update from banks
we assume mortage interst = 4% for our calculation 

6. Renting expense ≈ 30% of After-Tax Income 

A recent Rentals.ca survey shows that more than 60% of renters already spend over 30% of their income on rent
So we assume renting expenses for renter is rougly 30% of the post tax income 

## citation 
“Current Toronto Mortgage Rates | Best Mortgage Rates in Canada - RATESDOTCA.” Rates.ca, rates.ca/mortgage-rates/toronto.

Melgar, Alejandro. “Around 30% of Canadian Renters Spend 50% of Income on Rent: Survey.” CityNews Calgary, 21 Dec. 2025, calgary.citynews.ca/2025/12/21/canadian-renters-30-percent-half-income-rent-survey/ 

“Perspectives on Labour and Income - Measuring Housing Affordability.” Statcan.gc.ca, 2025, www150.statcan.gc.ca/n1/pub/75-001-x/11106/9519-eng.htm. 


------------------------------------------------------------------------

# Real-World Application

Findings can informs:

### Policymakers

-   Rent relief targeting
-   Student debt programs
-   Liquidity buffers

### Universities

-   Emergency student grants
-   Financial literacy programming

### Financial Institutions

-   Risk-adjusted product design
-   Targeted advisory services

------------------------------------------------------------------------

#  Reproducibility

To reproduce results:

1.  Activate virtual environment
2.  Install packages
3.  Run notebook top-to-bottom

If kernel restarts, rerun all cells.

------------------------------------------------------------------------

# 🤖 AI Usage Disclosure

AI tools were used for: - Debugging environment setup - Refactoring code
structure - Suggesting model validation best practices - Improving
documentation clarity

All final analysis and modeling decisions were verified and executed by
the team.

------------------------------------------------------------------------

# Team

-   Amelia Ha
-   Jadyn Mo
-   Tamima Wadageri

