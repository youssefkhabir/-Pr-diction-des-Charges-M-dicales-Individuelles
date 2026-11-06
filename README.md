# 🏥 Individual Medical Charges Prediction

[![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-1.2%2B-orange.svg)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/Academic-Master%20ISI-green.svg)](#)

> **Course:** Machine Learning / Regression — Master ISI  
> **Topic:** Actuarial Modeling & Predictive Econometrics for Healthcare Costs  
> **Interactive Plan:** [`plan/index.html`](plan/index.html)

---

## 📌 1. Project Overview

This project implements an end-to-end Machine Learning and regression pipeline on a US medical insurance dataset (`medical-charges.csv`, $N = 1,339$). The central objective is to predict individual annual healthcare charges (`charges`) based on biometric, demographic, and lifestyle indicators.

The study rigorously adheres to the 7-phase methodology detailed in the [Specification Charter](cahier_de_charges%20(1).pdf):
1. **Exploratory Data Analysis (EDA):** Univariate, bivariate, multivariate, and interaction analyses ($\text{BMI} \times \text{smoker}$).
2. **Data Cleaning & Leak-Free Preprocessing:** Missing values, deduplication, One-Hot Encoding, and `StandardScaler` (fit on train only).
3. **Regularized Linear Modeling:** Benchmark Ordinary Least Squares (OLS), Ridge ($L_2$), Lasso ($L_1$), and ElasticNet ($L_1 + L_2$).
4. **Model Evaluation & Residual Diagnostics:** RMSE, MAE, $R^2$, Adjusted $R^2$, residual normality, and homoscedasticity testing.
5. **Feature Selection:** Stepwise Backward Elimination based on `statsmodels` OLS Student t-test p-values ($\alpha = 0.05$), RFE, and Lasso zero-weights.
6. **Comparative Analysis:** All Features vs. Selected Features performance comparison and parsimony assessment.
7. **Synthesis & Perspectives:** Identification of top risk factors, model limitations, and non-linear perspectives (XGBoost, Random Forest).

---

## 🗂 2. Repository Structure

```text
Medical Cost Prediction/
│
├── cahier_de_charges (1).pdf      # Original academic project specification
├── requirements.txt               # Required Python packages and dependencies
├── README.md                      # Project documentation and setup guide
│
├── plan/                          # Interactive Academic Project Plan
│   └── index.html                 # Comprehensive visual plan with KaTeX & interactive checklist
│
├── data/                          # Dataset directory (recommended)
│   └── medical-charges.csv        # 1,339 records, 7 variables (exogenous + target)
│
└── medical_cost_prediction.ipynb  # Primary Jupyter Notebook implementing all 7 phases
```

---

## ⚙️ 3. Prerequisites & Environment Setup

Ensure you have **Python 3.8 or higher** installed (Python 3.10+ recommended).

### Step 1: Clone or Navigate to the Project Folder
Open your terminal (PowerShell or Bash) and change into the project directory:
```powershell
cd "d:\work\Medical Cost Prediction"
```

### Step 2: Create a Virtual Environment
Isolating dependencies ensures a reproducible environment:

**On Windows (PowerShell):**
```powershell
python -m venv venv
```

**On macOS / Linux:**
```bash
python3 -m venv venv
```

### Step 3: Activate the Virtual Environment

**On Windows (PowerShell):**
```powershell
.\venv\Scripts\Activate.ps1
```
> *Note for Windows:* If you encounter a script execution restriction, run:
> ```powershell
> Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
> .\venv\Scripts\Activate.ps1
> ```

**On Windows (Command Prompt):**
```cmd
venv\Scripts\activate.bat
```

**On macOS / Linux:**
```bash
source venv/bin/activate
```

### Step 4: Upgrade Pip & Install Dependencies
With the virtual environment active, run:
```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### Step 5: Register the Virtual Environment Kernel for Jupyter
Ensure Jupyter recognizes this virtual environment:
```bash
python -m ipykernel install --user --name=med-cost-env --display-name="Python (Med Cost Prediction)"
```

---

## 📊 4. Dataset Placement

The project requires the dataset `medical-charges.csv`:
* Place `medical-charges.csv` either directly in the root folder:
  ```text
  d:\work\Medical Cost Prediction\medical-charges.csv
  ```
  or inside a `data/` folder:
  ```text
  d:\work\Medical Cost Prediction\data\medical-charges.csv
  ```

### Data Dictionary

| Feature | Type | Description | Permissible Range |
| :--- | :--- | :--- | :--- |
| `age` | Numerical (Int) | Age of the primary insurance beneficiary | 18 – 64 years |
| `sex` | Categorical | Biological sex | `female`, `male` |
| `bmi` | Numerical (Float) | Body Mass Index ($kg / m^2$) | 15.96 – 53.13 |
| `children` | Numerical (Int) | Number of covered dependents | 0 – 5 |
| `smoker` | Categorical | Tobacco smoking status | `yes`, `no` |
| `region` | Categorical | US geographic residential area | `southwest`, `southeast`, `northwest`, `northeast` |
| **`charges`** | **Numerical (Target)** | **Billed medical insurance expenses** | **\$1,121.87 – \$63,770.43** |

---

## 🚀 5. How to Run the Project

You can run and inspect the project through three primary methods:

### Method A: Running via VS Code (Recommended)
1. Open the project folder in **Visual Studio Code**:
   ```powershell
   code .
   ```
2. Open the file `medical_cost_prediction.ipynb`.
3. In the top-right corner of the notebook editor, click **Select Kernel** $\rightarrow$ **Python Environments...** $\rightarrow$ select `med-cost-env` (or `./venv/Scripts/python.exe`).
4. Click **Run All** or execute each cell step-by-step using `Shift + Enter`.

---

### Method B: Running via Jupyter Notebook / JupyterLab
1. Activate your virtual environment:
   ```powershell
   .\venv\Scripts\Activate.ps1
   ```
2. Launch the Jupyter server:
   ```bash
   jupyter lab
   # or
   jupyter notebook
   ```
3. Your browser will automatically open at `http://localhost:8888`.
4. Click to open `medical_cost_prediction.ipynb`.
5. Under the **Kernel** menu, select **Change Kernel** $\rightarrow$ **Python (Med Cost Prediction)**.
6. Execute cells sequentially from top to bottom.

---

### Method C: Viewing the Interactive Academic Specification Plan
An interactive, academic HTML monograph summarizing every mathematical equation, task checklist, and project milestone is located in the `plan/` directory:

1. Open `plan/index.html` directly in any web browser:
   - On Windows: double-click `plan/index.html` or run:
     ```powershell
     Start-Process "plan\index.html"
     ```
   - On macOS:
     ```bash
     open plan/index.html
     ```
   - On Linux:
     ```bash
     xdg-open plan/index.html
     ```
2. Features of the plan page:
   - Mathematical formula cards (KaTeX-rendered loss functions for OLS, Ridge, Lasso, ElasticNet).
   - Architectural workflow diagram.
   - Interactive success criteria checklist with dynamic progress calculation.
   - Print-ready styling for generating PDF reports.

---

## 🔬 6. Notebook Execution Flow (10 Sections)

The execution in `medical_cost_prediction.ipynb` strictly mirrors the assignment roadmap:

1. **Section 1 — Introduction & Dataset Overview:** Problem formulation and actuarial context.
2. **Section 2 — Library Imports & Reproducibility:** Imports (`pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn`, `statsmodels`) and fixed random seeds.
3. **Section 3 — Data Ingestion & Integrity Audits:** Verifying dimensions, data types, and initial sample distributions.
4. **Section 4 — Exploratory Data Analysis (EDA):**
   * Univariate plots (KDE histograms, boxplots, countplots).
   * Bivariate relationships (`charges` vs. covariates).
   * Key interaction analysis: $\text{BMI} \times \text{smoker}$ compounding effect.
   * Correlation heatmap and pairplots.
   * Tukey's IQR outlier detection.
5. **Section 5 — Data Cleaning & Preprocessing:**
   * Null checks (`df.isnull().sum()`) and deduplication (`df.drop_duplicates()`).
   * Categorical encoding (binary for `sex`/`smoker`, One-Hot with `drop_first=True` for `region`).
   * Numerical scaling via `StandardScaler` (anti-leakage: fit on train, transform test).
   * 80% / 20% Train/Test split (`random_state=42`).
6. **Section 6 — Regularized Linear Modeling:**
   * Linear Regression (OLS).
   * Ridge Regression ($L_2$).
   * Lasso Regression ($L_1$, sparsity generation).
   * ElasticNet Regression ($L_1 + L_2$).
   * 5-fold cross-validation and hyperparameter tuning ($\alpha$).
7. **Section 7 — Model Evaluation & Residual Diagnostics:**
   * Metrics table: RMSE, MAE, $R^2$, and Adjusted $R^2$.
   * Residual distribution (checking $\epsilon \sim \mathcal{N}(0, \sigma^2)$).
   * Residuals vs. Fitted plot (evaluating homoscedasticity).
   * Actual vs. Predicted scatter plot with $y = x$ line.
8. **Section 8 — Feature Selection:**
   * Step-by-step Backward Elimination with `statsmodels.api.OLS` dropping $p > 0.05$.
   * Comparison with Scikit-Learn RFE and Lasso zero-coefficient weights.
9. **Section 9 — Comparative Analysis (All vs. Selected Features):**
   * Multi-model retraining on the selected feature subspace.
   * MultiIndex comparison table and grouped bar charts.
   * Parsimony trade-off assessment (Occam's razor).
10. **Section 10 — Synthesis, Limitations & Future Perspectives:**
    * Key takeaways (smoking premium, BMI non-linear threshold).
    * Limitations (linear assumptions, missing clinical history).
    * Recommended next steps (Random Forest, XGBoost, polynomial features).

---

## 🛠 7. Troubleshooting & FAQ

* **Issue: `ModuleNotFoundError: No module named 'scipy'` or `'sklearn'`**
  * *Solution:* Verify your virtual environment is active (`(venv)` shown in prompt) and run `pip install -r requirements.txt`. In Jupyter, ensure you selected the `med-cost-env` kernel.
* **Issue: `FileNotFoundError: [Errno 2] No such file or directory: 'medical-charges.csv'`**
  * *Solution:* Check that the dataset file is placed in the project root directory or update the path in Section 3 of the notebook to match your file location (`pd.read_csv('medical-charges.csv')` or `pd.read_csv('data/medical-charges.csv')`).
* **Issue: PowerShell says `Execution of scripts is disabled on this system`**
  * *Solution:* Run `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` in the current PowerShell session and reactivate the virtual environment.

---

## 👥 8. Author & Academic Context

* **Program:** Master ISI (Informatique des Systèmes Intelligents)
* **Module:** Machine Learning & Regression
* **Specification Document:** [`cahier_de_charges (1).pdf`](cahier_de_charges%20(1).pdf)
* **Generated Project Plan:** [`plan/index.html`](plan/index.html)
