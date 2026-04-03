# Counterfactual Inflation Analysis: Ukraine and the Euro Area

## Project Overview

This project investigates how Ukrainian inflation would have evolved if Ukraine had been part of the Euro Area.

The objective is to construct a counterfactual inflation path by combining:
- Ukrainian inflation data,
- Euro Area inflation dynamics,
- a structural VAR framework.

---

## Methodology

The analysis follows three main steps:

1. **Data construction**
   - Ukraine CPI (monthly) is converted into year-on-year inflation.
   - Euro Area inflation is computed as the average across countries.
   - Industrial production is used as a proxy for output.

2. **VAR estimation**
   - Two VAR models are estimated:
     - Ukraine (inflation, output)
     - Euro Area (inflation, output)

3. **Counterfactual simulation**
   - Ukraine keeps its own supply shocks.
   - Euro Area demand shocks are imposed.
   - A dynamic simulation produces the counterfactual inflation path.

---

## Key Results

- Counterfactual inflation is significantly **less volatile**.
- The **average inflation level remains similar**.
- Differences are strongest during crisis periods.

This suggests that monetary regime mainly affects **inflation stability**, not its level.

---

## Limitations

- Short sample period (post-2021)
- Industrial production used as output proxy
- Structural identification relies on Cholesky decomposition

---

## Files

- `notebook.ipynb` → main analysis
- `data/` → input datasets
- `figures/` → generated plots
- `output/` → results and tables

---

## Author

Yoav Cohen  
M2 Quantitative Methods in Finance  
Université Paris 1 Panthéon-Sorbonne