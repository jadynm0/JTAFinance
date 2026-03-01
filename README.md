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

You only need the notebook + dataset (plus the packages below).

------------------------------------------------------------------------
# Setup Instructions (Mac / Windows / Linux)

## 1. Clone or Download
If you are using Git:

``` bash
git clone <your_repo_url>
cd JTAFinance
```

Or download the ZIP and open the folder.
If you downloaded a ZIP:
- Extract the ZIP
- Open the extracted folder
- Make sure `Datathon-Personal-Finance.ipynb` and `personal_finance_dataset.xlsx` are both inside that folder


## 2. Create Virtual Environment

A virtual environment keeps the project packages separate from the rest of your computer.

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
If PowerShell blocks activation, run this once in PowerShell and try again:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

After activation, your terminal should show something like `(.venv)` at the beginning of the line.

## 3. Install Required Packages

``` bash
python -m pip install --upgrade pip
python -m pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter ipykernel
```
or 
``` bash
python3 -m pip install --upgrade pip
python3 -m pip install -r requirements.txt
```

Packages used in the notebook:
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `openpyxl`
- `jupyter`
- `ipykernel`

### 4) Make the environment show up as a notebook kernel

Run:

```bash
python -m ipykernel install --user --name jtafinance-venv --display-name "Python (jtafinance-venv)"
```

This makes it easier to select the correct kernel in VS Code or Jupyter.

------------------------------------------------------------------------
# How to Run the Project

## Option A - VS Code (Recommended)

1. Open the project folder in VS Code
2. Open `Datathon-Personal-Finance.ipynb`
3. In the top right, select the kernel named:
   - **Python (jtafinance-venv)**
   - or your `.venv` Python environment
4. Run the notebook from top to bottom
   - Use **Run All** if you want everything
   - Or run cell by cell in order


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

## 3. Simulate shocks

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

## Expected outputs

If the notebook runs correctly, you should get:
- printed data previews
- summary tables by age group
- bar charts for different shock scenarios
- permutation importance chart
- persona risk chart
- stress test line charts

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
“Average Rental Price in Toronto, on & Market Trends | Zillow Rental Manager.” Zillow.com, 2024, www.zillow.com/rental-manager/market-trends/toronto-on/. 

Canada, Financial Consumer Agency of. “Government of Canada.” Canada.Ca, / Gouvernement du Canada, 20 Oct. 2025, www.canada.ca/en/financial-consumer-agency/services/savings-investments/setting-up-emergency-funds.html. 

“Calculating GDS / TDS.” CMHC, 31 Mar. 2018, www.cmhc-schl.gc.ca/professionals/project-funding-and-mortgage-financing/mortgage-loan-insurance/calculating-gds-tds.

“Current Toronto Mortgage Rates | Best Mortgage Rates in Canada - RATESDOTCA.” Rates.ca, rates.ca/mortgage-rates/toronto.

Immigration, Refugees and Citizenship Canada. “Prepare Financially.” Canada.Ca, / Gouvernement du Canada, 15 July 2025, www.canada.ca/en/immigration-refugees-citizenship/services/settle-canada/prepare-financially.html. 

Naik, Miral. “Debt-To-Income Ratio: What’s It All About?” Consolidated Credit Counselling Services of Canada, Consolidated Credit Canada, 23 July 2025, www.consolidatedcreditcanada.ca/financial-news/debt-to-income-ratio-whats-it-all-about/ 

Melgar, Alejandro. “Around 30% of Canadian Renters Spend 50% of Income on Rent: Survey.” CityNews Calgary, 21 Dec. 2025, calgary.citynews.ca/2025/12/21/canadian-renters-30-percent-half-income-rent-survey/ 

“Perspectives on Labour and Income - Measuring Housing Affordability.” Statcan.gc.ca, 2025, www150.statcan.gc.ca/n1/pub/75-001-x/11106/9519-eng.htm. 


------------------------------------------------------------------------

# Real-World Application

Findings can informs:

### Policymakers

- Identify households most vulnerable to income or rent shocks
- Design targeted emergency savings programs
- Prioritize rental assistance or income stabilization support

### Universities

-  Detect high-risk student populations
- Improve financial literacy programming
- Develop emergency grant allocation strategies

### Financial Institutions

-  Improve risk assessment models
- Design savings buffer products
- Identify clients vulnerable to rate shocks

## Economic Planning

- Stress-test population-level financial resilience
- Evaluate how inflation or income volatility affects different age groups

------------------------------------------------------------------------

#  Reproducibility

Before running, confirm all of these are true:

- Python is installed
- The virtual environment is activated
- All packages are installed
- The notebook and Excel file are in the same folder
- The Excel file is named `personal_finance_dataset.xlsx`
- The Excel sheet is named `datathon_finance`
- The correct kernel is selected
- You are running cells from top to bottom

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

