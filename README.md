# Counterfactual Inflation Analysis: Ukraine vs Euro Area

##  Project Overview

This project is developed as part of the **Quantitative Methods in Finance** course (M2, Université Paris 1 Panthéon-Sorbonne).

The objective is to construct a **counterfactual inflation path for Ukraine** under the hypothetical scenario in which Ukraine had been part of the **Euro Area**.

The analysis combines:
- a **monetary regime study**,
- a **structural macroeconometric model (VAR/SVAR)**,
- and a **counterfactual simulation based on shock replacement**.

---

## Research Question

> How would Ukraine’s inflation dynamics have evolved if its monetary policy had been governed by the European Central Bank?

---

##  Methodology

The approach follows three main steps:

### 1. Monetary Regime Analysis (Part A)

We document Ukraine’s monetary regimes (exchange rate regimes, crises, inflation targeting) and show that the effect of Euro Area membership is **time-varying**.

---

### 2. Econometric Framework (Part B)

We estimate a **bivariate VAR model** for both Ukraine and the Euro Area using:

- Inflation (year-on-year)
- Output proxy (industrial production growth)

We then apply a **Blanchard-Quah identification** to decompose shocks into:
- **Demand shocks** (no long-run effect on output)
- **Supply shocks** (permanent effects)

---

### 3. Counterfactual Simulation

We construct a counterfactual path where:

- Ukraine **keeps its own supply shocks**
- but **inherits Euro Area demand shocks**

Formally:

e^{CF}_{d,t} = (1 - τ_t)e^{UKR}_{d,t} + τ_t e^{EA}_{d,t}

e^{CF}_{s,t} = e^{UKR}_{s,t}

where τ_t captures the time-varying intensity of Euro Area membership.

---

##  Data

### Core datasets (provided)
- Euro Area inflation (ECB / panel)
- Ukraine CPI (monthly index → reconstructed YoY inflation)

### External datasets
- Industrial Production Index (Eurostat):
  - Euro Area (EA20)
  - Ukraine (or external source if missing)

---

##  Project Structure

yoav_qmf_project/
│
├── notebook.ipynb        # Main analysis
├── data/                 # Raw data (Eurostat + external)
├── figures/              # Output plots
├── output/               # Processed datasets
├── requirements.txt      # Dependencies
└── README.md             # Project documentation

---

##  Installation

Create environment:

```bash
conda create -n qmf_env python=3.11
conda activate qmf_env
pip install -r requirements.txt'''

## Author

 Yoav Cohen
M2 Quantitative Finance
Université Paris 1 Panthéon-Sorbonne