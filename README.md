# JTAFinance
Datathon!
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

The goal:\
\> Identify who is financially vulnerable under 55 in Canada and what
can be done.

------------------------------------------------------------------------

# 📂 Repository Structure

    JTAinance/
    │
    ├── Datathon-Personal-Finance.ipynb
    ├── personal_finance_dataset.xlsx
    ├── README.md
    └── .venv/

You only need the notebook and dataset to run the project.


# Setup Instructions (Mac / Windows / Linux)

## 1. Clone or Download

``` bash
git clone <your_repo_url>
cd JTFinance
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


## 3️⃣ Install Required Packages

``` bash
python -m pip install --upgrade pip
python -m pip install numpy pandas matplotlib seaborn scikit-learn openpyxl
```

Required libraries: - numpy - pandas - matplotlib - seaborn -
scikit-learn - openpyxl (for Excel reading)


# How to Run the Project

## Option A --- VS Code (Recommended)

1.  Open folder in VS Code
2.  Install extensions if prompted:
    -   Python
    -   Jupyter
3.  Open `Datathon-Personal-Finance.ipynb`
4.  Select kernel: `.venv (Python 3.x)`
5.  Click **Run All**



## Option B --- Jupyter Notebook

``` bash
python -m pip install jupyter
jupyter notebook
```

Open the notebook and run all cells top to bottom.


#  What the Notebook Does

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

-   \< 3 months liquidity runway\
    OR\
-   Housing burden \> 35%\
    OR\
-   Debt-to-income \> 50%\
    OR\
-   Skipped payments

------------------------------------------------------------------------

## 3. Predictive Modeling

Model: **Random Forest Classifier**

Validation: - Train/Test split - ROC-AUC - F1 Score - Confusion Matrix

Interpretability: - Random Forest Feature Importance - Permutation
Importance

------------------------------------------------------------------------

## 4. Stress Testing

Simulates economic shocks:

-   0% → 30% expense inflation

Outputs: - At-risk rate vs shock curve - Newly vulnerable share - Age
group breakdown

------------------------------------------------------------------------

## 5. Financial Personas (Segmentation)

Uses KMeans clustering on:

-   Liquidity Months
-   Housing Burden
-   DTI Ratio
-   Income
-   Total Liquidity

Produces: - 5 distinct financial personas - Risk % per persona - Visual
summary

------------------------------------------------------------------------

# Real-World Application

Findings inform:

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
-   Tamima 

------------------------------------------------------------------------

# Final Goal

This project answers:

> Who is financially vulnerable under 55 in Canada,\
> what drives that vulnerability,\
> how shocks amplify risk,\
> and what targeted interventions can improve resilience?
r