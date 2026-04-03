# Counterfactual Inflation Analysis: What If Ukraine Had Been Part of the Euro Area?

**Author:** Yoav Cohen  
**Course:** Quantitative Methods in Finance — M2 Research  
**Professor:** Eric Vansteenberghe (Banque de France & Université Paris 1 Panthéon-Sorbonne)  
**Academic Year:** 2025–2026

---

## Project Overview

This project constructs a **counterfactual inflation path** for Ukraine under the hypothesis that it had been a member of the Euro Area, using a Structural VAR framework.

The analysis addresses two questions:
1. **Part A** — When did Ukraine have genuine monetary sovereignty, and when was its policy de facto constrained by an exchange-rate peg?
2. **Part B** — What would Ukrainian inflation have looked like under ECB monetary policy?

## Methodology

The counterfactual is built in three steps:

1. **Monetary regime chronology (Part A):** A documented classification of the NBU's exchange-rate regime from 2000 to 2025, identifying de facto peg periods, devaluation episodes, capital controls, and the 2016 transition to inflation targeting. Sources include IMF AREAER reports, NBU publications, and Calvo & Reinhart (2002).

2. **Trivariate SVAR estimation (Part B):** A VAR is estimated on three variables — EA industrial production growth, EA average inflation, and Ukraine inflation — with Cholesky identification (EA block-exogenous to Ukraine). This yields three structural shocks: EA supply, EA demand, and Ukraine-specific.

3. **Counterfactual simulation:** Ukraine's idiosyncratic shocks (monetary policy, exchange-rate pass-through) are set to zero. The counterfactual inflation path retains only the EA-wide shocks that would have affected Ukraine as an EA member.

The identification strategy is consistent with Part A: during peg periods, the estimated Ukraine-specific shocks are empirically small (monetary independence was already constrained), so the counterfactual differs little from actual inflation. During devaluation episodes and the inflation-targeting period, the shocks are large, generating a visible gap.

## Key Results

- Counterfactual inflation is significantly **less volatile** than actual Ukrainian inflation.
- The largest gaps occur during the **2008–09 GFC** and **2014–15 Crimea crisis**, when exchange-rate devaluations amplified domestic inflation — an adjustment channel unavailable under EA membership.
- The gap **narrows after 2016**, when the NBU's inflation-targeting reform partially replicated the credibility benefits of EA membership.
- The average inflation level remains broadly similar, suggesting that monetary regime mainly affects **inflation stability**, not its long-run level.

## Repository Structure

```
qmf-ukraine-counterfactual/
├── notebook.ipynb                          # Main analysis (Part A + Part B)
├── requirements.txt                        # Python dependencies
├── README.md                               # This file
├── data/
│   ├── data_ecb_hicp_panel.csv             # ECB HICP panel (11 EA countries, YoY %)
│   ├── data_ukraine_cpi_raw.csv            # Ukraine CPI (MoM index, SSSU via SDMX)
│   └── industrial_production.csv           # EA20 Industrial Production (Eurostat)
├── figures/                                # Generated plots (15 figures)
│   ├── 01_inflation_comparison.png
│   ├── 02_rolling_correlation.png
│   ├── ...
│   └── 15_robustness_bivariate.png
└── output/                                 # Generated tables and results
    ├── table1_regime.csv
    ├── table3_adf.csv
    ├── structural_shocks.csv
    └── counterfactual_results.csv
```

## Data Sources

| Dataset | Source | Description |
|---------|--------|-------------|
| `data_ecb_hicp_panel.csv` | ECB Data Portal | Monthly HICP YoY inflation (%) for 11 EA countries (AT, BE, DE, ES, FI, FR, GR, IE, IT, NL, PT), Jan 2000 – Dec 2025 |
| `data_ukraine_cpi_raw.csv` | State Statistics Service of Ukraine (SSSU) via SDMX | Monthly CPI index (previous month = 100), Feb 2000 – Dec 2025 |
| `industrial_production.csv` | Eurostat, series `STS_INPR_M` | Monthly Industrial Production Index (2015=100), EA20 aggregate, calendar-adjusted, sectors B–D. Required for supply/demand shock decomposition in the SVAR |

The first two datasets are from the course repository. The industrial production series is the **mandatory external dataset**, sourced from Eurostat to enable the Bayoumi–Eichengreen (1993) identification of supply vs. demand shocks via the Blanchard–Quah (1989) long-run restriction framework.

## Reproduction Instructions

### Prerequisites

- Python 3.11+
- Conda (recommended)

### Setup

```bash
git clone https://github.com/<your-username>/qmf-ukraine-counterfactual.git
cd qmf-ukraine-counterfactual

# Create and activate conda environment
conda create -n qmf_env python=3.11 -y
conda activate qmf_env

# Install dependencies
pip install -r requirements.txt
```

### Run

```bash
jupyter notebook notebook.ipynb
```

Execute all cells sequentially. The notebook generates all figures in `figures/` and all result tables in `output/` automatically. No manual data download or preprocessing is required — all three datasets are provided in `data/`.

## References

- Bayoumi, T. & Eichengreen, B. (1993). "Shocking aspects of European monetary integration." In *Adjustment and Growth in the European Monetary Union*, Cambridge University Press.
- Blanchard, O. & Quah, D. (1989). "The Dynamic Effects of Aggregate Demand and Supply Disturbances." *American Economic Review*, 79(4).
- Calvo, G. & Reinhart, C. (2002). "Fear of Floating." *Quarterly Journal of Economics*, 117(2).
- Ciccarelli, M. & Mojon, B. (2010). "Global Inflation." *Review of Economics and Statistics*, 92(3).
- De Grauwe, P. (2012). "The Governance of a Fragile Eurozone." *Australian Economic Review*, 45(3).
- Frankel, J. & Rose, A. (1998). "The Endogeneity of the OCA Criteria." *Economic Journal*, 108(449).
- Giavazzi, F. & Pagano, M. (1988). "The Advantage of Tying One's Hands." *European Economic Review*, 32(5).
- Kilian, L. & Lütkepohl, H. (2017). *Structural Vector Autoregressive Analysis.* Cambridge University Press.
- Lucas, R. (1976). "Econometric Policy Evaluation: A Critique." *Carnegie-Rochester Conference Series*, 1.
- Mundell, R. (1961). "A Theory of Optimum Currency Areas." *American Economic Review*, 51(4).