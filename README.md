<div align="center">

# 🔌 European E-Mobility Market Dynamics

**Drivers · Regulations · Infrastructure Analysis for Informed Charging Infrastructure Development**

[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![Libraries](https://img.shields.io/badge/Libraries-Pandas%20%7C%20NumPy%20%7C%20SciPy%20%7C%20Scikit--learn%20%7C%20Matplotlib-informational)]()
[![Institution](https://img.shields.io/badge/Institution-RWTH%20Aachen-darkblue)]()
[![Partner](https://img.shields.io/badge/Industry%20Partner-Numbat%20GmbH-green)]()
[![Thesis](https://img.shields.io/badge/Type-Master's%20Thesis-orange)]()

</div>

---

## 📌 Overview

This master's thesis — conducted at **RWTH Aachen University** in collaboration with **[Numbat GmbH](https://www.numbat.de/)**, a European fast-charging infrastructure company — investigates the key factors driving EV adoption and charging infrastructure growth across **14 European countries**.

The research combines a **quantitative regression model** (Python) with **structured qualitative analysis** and a **multi-criteria incentive rating framework** to deliver actionable intelligence for stakeholders — EV manufacturers, charging infrastructure providers, and policymakers.

> **Why it matters:** Europe has a 2035 zero-emissions target. Understanding *which* policy, infrastructure, and economic factors actually move the market is essential for companies like Numbat deciding where to invest next.

---

## 🎯 Research Questions

1. What are the **quantitative key factors** driving differential success in the European e-mobility market ramp-up?
2. What are the **qualitative key factors** — socio-cultural and policy-driven — that shape market dynamics?
3. What role do **regulatory incentives** (subsidies, tax rebates, grants) play in EV and charging infrastructure adoption?

---

## 🗂️ Repository Structure

```
E-Mobility_Market_Dynamics_Model/
│
├── Emobility_Market_Dynamics.ipynb   # Full analysis pipeline
│                                      # (data collection → EDA → correlation
│                                      #  → OLS regression → incentive scoring)
└── README.md                          # This file
```

---

## 🔬 Methodology

The study uses a **three-track mixed-methods approach**:

```
Data Sources                  Analysis Tracks                   Output
─────────────────────         ──────────────────────────        ──────────────────────────────
Eurostat                  ──► QUANTITATIVE                  ──► OLS Regression Model
European Alt. Fuels Obs.       Pearson correlation                (R² = 0.735, 14 variables,
IEA Global EV Explorer         Multiple linear regression          96 observations)
ACEA Reports                   Descriptive statistics
Numbat GmbH (internal) ───►
                               QUALITATIVE                    ──► 9 Socio-cultural &
Country-specific DBs      ──►  Thematic analysis                  Policy-related drivers
                               Recurring factor identification     (consumer acceptance,
                               Cross-country comparison            PPPs, standardisation...)

ACEA Incentive Data       ──► INCENTIVE SCORING              ──► Country rankings across
                               Multi-criteria rating (5 criteria)  14 EU markets
                               Weighted scoring: Market           (High / Medium / Low)
                               Influence 40%, Financial
                               Impact 30%, Access 15%,
                               Scope 10%, Duration 5%
```

### Variables in the Regression Model

| Category | Variables |
|---|---|
| **Dependent** | EV Registrations |
| **Demographic** | Inhabitants |
| **Economic** | GDPI, AC/DC/HPC Charging Prices, Energy Cost |
| **Infrastructure** | AC Points, DC Points, HPC Points, Total Publicly Charged Electricity (kWh), EVs Charging Only in Public |
| **Home Charging** | Amount of EVs in Wallbox Households, Realistic Share of Wallbox Owners, Population Share with Home-Charging Possible |
| **Environmental** | Environmental Performance Index (EPI) Score |

---

## 📊 Results

### 1. Correlation Analysis

The heatmap below shows Pearson correlations between EV registrations and all independent variables.

![Correlation Matrix Heatmap](correlation_heatmap.png)

**Key correlations with EV Registrations:**

| Variable | Pearson r | P-value | Interpretation |
|---|---|---|---|
| Amount of EVs in Wallbox Households | **0.795** | < 0.00001 | Strongest predictor — private charging access drives adoption |
| Total Publicly Charged Electricity (kWh) | **0.737** | < 0.00001 | More public charging energy = more EVs |
| DC Points | **0.706** | < 0.00001 | Fast charging density strongly linked to uptake |
| Amount of EVs Charging Only in Public | **0.714** | < 0.00001 | Public infrastructure demand co-moves with registration |
| HPC Points | **0.676** | < 0.00001 | High-power charging presence correlated with adoption |
| GDPI | 0.514 | < 0.0001 | Moderate — economic prosperity helps but not dominant |
| AC Charging Price | 0.074 | 0.561 | Negligible — price alone doesn't move the needle |
| DC / HPC Charging Price | ~0.00 / -0.07 | >0.5 | No meaningful price effect on adoption |

> **Insight:** Infrastructure availability — not price — is the primary driver of EV adoption. Charging price changes matter less than whether charging exists at all.

---

### 2. Regression Model (OLS)

**Model fit: R² = 0.735 · Adjusted R² = 0.692 · N = 100 observations**

| Variable | Coefficient | P-value | Significance |
|---|---|---|---|
| Amount of EVs in Wallbox Households | 0.4313 | 0.000 | ★★★ Highly significant |
| Inhabitants | 0.1401 | 0.007 | ★★ Significant |
| AC Charging Price | -0.1477 | 0.057 | ✦ Marginally significant (negative) |
| Amount of EVs Charging Only in Public | -0.1751 | 0.095 | ✦ Marginal |
| GDPI, DC Points, HPC Points, etc. | — | > 0.1 | Not significant independently |

The model explains **73.5% of variance** in EV registrations. Two variables stand out:
- **Wallbox household access** is the dominant driver: convenience of home charging is what tips purchasing decisions
- **Population size** is a baseline predictor — larger countries have more EVs, but not proportionally more than private charging would predict
- **AC charging price** shows a subtle negative effect — higher public charging costs marginally deter adoption

> **Why didn't more variables reach significance?** High multicollinearity between infrastructure variables (DC points, HPC points, publicly charged energy) means they share explanatory power. Each is individually correlated with EV uptake, but the regression allocates that power to the most independent predictor (wallbox access). This is an honest model limitation, addressed through the qualitative and incentive analysis tracks.

---

### 3. Comparative Incentive Analysis

The chart below maps EV market ratings and charging infrastructure ratings against key quantitative outputs (EV registrations, DC/HPC/AC charging points, EPI score) for 14 European countries.

![Comparative Analysis of Incentives and Key Quantitative Factors](comparative_analysis.png)

**Three clusters emerge:**

| Cluster | Countries | Pattern |
|---|---|---|
| 🟢 **High incentives → Strong market growth** | Germany, Norway, France, Austria | High EV market ratings, robust EV registrations — but charging infrastructure often lags market demand |
| 🟡 **Moderate incentives → Mixed outcomes** | Spain, Italy, Belgium, Netherlands | Spain and Belgium show balanced growth; Italy and Netherlands show gaps between market demand and infrastructure |
| 🔵 **Balanced moderate incentives → Steady growth** | UK, Finland, Denmark, Sweden, Switzerland, Czech Republic | Conservative but stable — medium ratings across both market and infrastructure |

> **Key finding for Numbat GmbH:** High-incentive markets (Germany, Norway, France) have strong EV demand but *under-developed* charging infrastructure relative to that demand — representing the best near-term investment opportunity for fast-charging providers.

---

### 4. Qualitative Findings — 9 Key Factors

Beyond what quantitative data can capture, the analysis identified **9 structural drivers** across two categories:

**Policy-Related Drivers**
- **Local & Regional Incentives** — Tax rebates and subsidies (Germany, Netherlands) directly accelerate adoption, but require coordinated policy frameworks to be effective
- **Technological Advancements** — Battery improvements and fast-charging tech only translate to adoption when paired with supportive infrastructure policy (Norway's fast-charging investment is the model)
- **Public-Private Partnerships** — Nantes and Hamburg demonstrate that PPPs resolve the financing gap for infrastructure in multi-family dwellings and underserved areas
- **Standardisation** — Uniform connectors (Type 2 mandate) and protocols reduce market fragmentation, lower costs, and enable faster deployment
- **Geographical Alignment** — Matching charging infrastructure to local renewable energy (wind in Nordics, solar in Southern Europe) improves both sustainability and economics

**Socio-Cultural Drivers**
- **Consumer Acceptance** — Safety concerns, range anxiety, and recharging time remain active barriers; transparent policies and demonstration projects are needed to build trust
- **Socio-Demographic Factors** — Higher-income, educated, urban households lead adoption; policies targeting lower-income and rural populations are needed for broader uptake
- **Total Cost of Ownership** — BEVs are cost-competitive over 10 years, but high upfront cost still deters buyers without sufficient incentive design
- **Data Availability** — Real-time charging station data reduces range anxiety and enables dynamic pricing; markets with better data infrastructure show higher utilisation rates

---

## 💡 Key Conclusions

1. **Home charging infrastructure is the single most important lever** — wallbox access in private households predicts EV registrations more strongly than any other factor (r = 0.795)
2. **DC fast-charging density is the most important public infrastructure variable** — strongly correlated with adoption (r = 0.706) and critical for reducing range anxiety on longer journeys
3. **Price alone doesn't determine adoption** — charging price has near-zero correlation with EV registrations; availability and convenience matter far more
4. **Financial incentives drive demand, but not always infrastructure** — Germany has strong market growth from incentives, but infrastructure investment has not kept pace, creating an exploitable gap
5. **European markets are not homogeneous** — a single pan-European model cannot predict country-level outcomes; regional qualitative factors carry substantial weight that quantitative models underestimate

---

## 🧰 Tech Stack

```python
# Core analysis
import pandas as pd          # Data collection, cleaning, transformation
import numpy as np           # Numerical computation
from scipy import stats      # Pearson correlation, p-values
import statsmodels.api as sm # OLS regression, VIF, diagnostic tests
from sklearn.linear_model import LinearRegression  # Model building

# Diagnostics
# White test (heteroscedasticity), Durbin-Watson (autocorrelation),
# Ramsey RESET (specification), VIF (multicollinearity)

# Visualisation
import matplotlib.pyplot as plt
import seaborn as sns         # Correlation heatmap

# Data sources
# Eurostat, European Alternative Fuels Observatory, IEA Global EV Explorer,
# ACEA, country-specific databases, Numbat GmbH internal data (2020–2023)
```

---

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/itsViru/E-Mobility_Market_Dynamics_Model.git
cd E-Mobility_Market_Dynamics_Model

# Install dependencies
pip install pandas numpy scipy scikit-learn statsmodels matplotlib seaborn jupyter

# Launch the notebook
jupyter notebook Emobility_Market_Dynamics.ipynb
```

The notebook is fully self-contained with inline comments explaining each analysis step.

---

## ⚠️ Limitations & Honest Model Assessment

| Limitation | Impact | How Addressed |
|---|---|---|
| High multicollinearity between infrastructure variables | Reduces individual statistical significance in regression | VIF analysis conducted; qualitative overlay compensates |
| Data unavailable for some countries/years | Reduced sample size for some variables (n=76–96) | Values estimated from correlated statistics where missing; documented |
| Cross-country regression on heterogeneous markets | Model captures average effects, not country-specific dynamics | Qualitative analysis provides country-level context |
| Regression explains 73.5% of variance | 26.5% unexplained — likely socio-cultural factors | Three-track methodology explicitly designed to capture the remainder |

---

## 🎓 Academic Context

| | |
|---|---|
| **Institution** | RWTH Aachen University — Institute of Technology and Innovation Management |
| **Chair** | Innovation, Strategy and Organization |
| **First Examiner** | Prof. Torsten-Oliver Salge, PhD |
| **Second Examiner** | Prof. Dr. Daniel Wentzel |
| **University Supervisor** | Katharina Thoms, M.Sc. |
| **Industry Supervisor** | Dr. Moritz Wollbrink (Numbat GmbH) |
| **Submission Date** | September 2024 |
| **Author** | Virendra Kowale (Matriculation No. 416856) |

---

## 📄 Note on Data

Data was collected from public European databases (Eurostat, European Alternative Fuels Observatory, IEA) and supplemented with proprietary data from Numbat GmbH. Proprietary data is not included in this repository. The notebook demonstrates the full analytical pipeline and methodology using the available data.
