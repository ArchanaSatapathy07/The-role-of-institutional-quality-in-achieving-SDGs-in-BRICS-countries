# The Role of Institutional Quality in Achieving SDGs in BRICS Countries

> Empirical analysis of governance effectiveness, economic growth, demographic change, and foreign investment on Sustainable Development Goal (SDG) performance in the expanded BRICS+ bloc.

## 📋 Table of Contents

- [Overview](#overview)
- [Key Findings](#key-findings)
- [Methodology](#methodology)
- [Repository Structure](#repository-structure)
- [Data Sources](#data-sources)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Citation](#citation)
- [License](#license)
- [Contact](#contact)

## 🌍 Overview

This study investigates the institutional foundations of sustainable development by analyzing how governance effectiveness, economic growth, demographic change, and foreign direct investment (FDI) influence SDG performance within the expanded BRICS+ bloc.

### BRICS+ Countries (2025)

As of January 2025, BRICS comprises **10 full member countries**:
- Brazil
- Russia
- India
- China
- South Africa
- Egypt
- Ethiopia
- Iran
- United Arab Emirates
- Indonesia

Together, these nations represent **over 40% of the global population**, making their institutional performance critical to global SDG attainment.

## 🔍 Key Findings

Our empirical analysis reveals:

| Variable | Effect | Coefficient | Significance |
|----------|--------|-------------|--------------|
| **Governance Effectiveness** | ✅ Positive | 0.0053 | p < 0.001 |
| **GDP per Capita** | ✅ Positive | 0.0061 | p < 0.001 |
| **Population Growth** | ⚠️ Negative | -0.0024 | p < 0.001 |
| **FDI Inflows** | ✅ Positive (weak) | 0.0042 | p < 0.10 |

### Main Insights

1. **Governance matters**: Strong institutions significantly improve SDG outcomes
2. **Economic capacity enables progress**: Higher GDP facilitates sustainability investments
3. **Demographic pressures constrain development**: Rapid population growth strains resources
4. **FDI requires strategic alignment**: Investment must target sustainable sectors

## 🔬 Methodology

### Econometric Approach

- **Model**: System Generalized Method of Moments (System GMM)
- **Period**: 2000-2023 (24 years)
- **Panel**: 10 countries, 240 observations
- **Estimation**: One-step System GMM with robust standard errors

### Model Specification

```
SDG_Index_it = β₀ + β₁·Gov_it + β₂·GDP_it + β₃·PopGrowth_it + β₄·FDI_it + εᵢₜ
```

Where:
- `Gov_it`: Government effectiveness score
- `GDP_it`: GDP per capita (2015 US$)
- `PopGrowth_it`: Annual population growth (%)
- `FDI_it`: FDI inflows (% of GDP)

### Diagnostic Tests

✅ **Multicollinearity**: All VIF < 2 (Mean VIF = 1.23)  
✅ **Cross-sectional dependence**: Pesaran CD test conducted  
✅ **Unit root**: Levin-Lin-Chu & Im-Pesaran-Shin tests  
✅ **Cointegration**: Pedroni & Kao tests confirm long-run relationships  
✅ **Instrument validity**: Hansen J-test passed  
✅ **Serial correlation**: Arellano-Bond AR(2) test passed

## 📁 Repository Structure

```
brics-sdg-research/
│
├── data/
│   ├── raw/                    # Original datasets
│   ├── processed/              # Cleaned and transformed data
│   └── README.md              # Data documentation
│
├── analysis/
│   ├── 01_data_cleaning.R     # Data preprocessing scripts
│   ├── 02_descriptive_stats.R # Descriptive analysis
│   ├── 03_diagnostics.R       # Panel diagnostics
│   ├── 04_gmm_estimation.R    # System GMM models
│   └── 05_visualization.R     # Result visualization
│
├── results/
│   ├── tables/                # LaTeX/CSV tables
│   ├── figures/               # Plots and charts
│   └── regression_output/     # Model outputs
│
├── docs/
│   ├── report.pdf             # Full research report
│   ├── methodology.md         # Detailed methodology
│   └── literature_review.md   # Literature synthesis
│
├── README.md                  # This file
├── LICENSE                    # MIT License
├── requirements.txt           # Python dependencies
├── environment.R              # R package dependencies
└── .gitignore
```

## 📊 Data Sources

| Dataset | Source | Variables | Period |
|---------|--------|-----------|--------|
| **SDG Index** | Sustainable Development Report | Overall SDG Score | 2000-2023 |
| **Governance Indicators** | World Bank WGI | Government Effectiveness | 2000-2023 |
| **Economic Data** | World Bank WDI | GDP per capita | 2000-2023 |
| **Demographic Data** | World Bank WDI | Population Growth | 2000-2023 |
| **Investment Data** | World Bank WDI | FDI Inflows | 2000-2023 |

### Data Access

- **World Bank WDI**: https://data.worldbank.org/
- **World Bank WGI**: https://info.worldbank.org/governance/wgi/
- **SDG Index**: https://dashboards.sdgindex.org/

## 🛠️ Installation

### R Environment

```R
# Install required packages
install.packages(c(
  "plm",           # Panel data models
  "systemfit",     # System GMM
  "lmtest",        # Diagnostic tests
  "tseries",       # Time series tests
  "ggplot2",       # Visualization
  "stargazer",     # Table formatting
  "dplyr",         # Data manipulation
  "haven"          # Data import
))
```

### Python Environment (Optional)

```bash
pip install -r requirements.txt
```

Contents of `requirements.txt`:
```
pandas>=1.3.0
numpy>=1.21.0
statsmodels>=0.13.0
matplotlib>=3.4.0
seaborn>=0.11.0
```

## 🚀 Usage

### Running the Complete Analysis

```R
# Set working directory
setwd("path/to/brics-sdg-research")

# Run full pipeline
source("analysis/01_data_cleaning.R")
source("analysis/02_descriptive_stats.R")
source("analysis/03_diagnostics.R")
source("analysis/04_gmm_estimation.R")
source("analysis/05_visualization.R")
```

### Reproducing Key Results

```R
# Load processed data
data <- read.csv("data/processed/panel_data.csv")

# Run System GMM
library(plm)
model <- pgmm(
  lnsdg ~ lag(lnsdg, 1) + gov + lngdp + pop + lag(lnfdi, 1),
  data = data,
  effect = "twoways",
  model = "onestep",
  transformation = "ld"
)

summary(model)
```

## 📈 Results

### Descriptive Statistics

| Variable | Mean | Std. Dev. | Min | Max |
|----------|------|-----------|-----|-----|
| SDG Index | 62.96 | 6.89 | 43.70 | 73.93 |
| Gov. Effectiveness | -0.096 | 0.558 | -1.21 | 1.60 |
| GDP (trillion $) | 1.58 | 2.95 | 0.017 | 17.2 |
| Pop. Growth (%) | 1.60 | 1.60 | -0.47 | 11.59 |
| FDI (% GDP) | 2.23 | 1.72 | -2.76 | 9.66 |

### Regression Results

Full regression output available in `results/tables/gmm_results.csv`

## 💡 Policy Implications

1. **Strengthen Governance Capacity**: Prioritize transparency, accountability, and administrative effectiveness
2. **Integrate Sustainability in Economic Planning**: Align growth strategies with environmental and social goals
3. **Manage Population Dynamics**: Invest in education, reproductive health, and urban planning
4. **Promote Sustainable Investment**: Implement ESG screening for FDI
5. **Enhance Regional Cooperation**: Share best practices across BRICS nations
6. **Build Data Systems**: Improve SDG monitoring and reporting capacity

## 📝 Citation

If you use this research or code, please cite:

```bibtex
@techreport{satapathy2025brics,
  author = {Satapathy, Archana},
  title = {The Role of Institutional Quality in Achieving SDGs in BRICS Countries},
  institution = {Indian Institute of Technology Kharagpur},
  type = {Bachelor's Thesis},
  year = {2025},
  month = {April},
  department = {Department of Humanities and Social Sciences},
  supervisor = {Mahalik, Mantu Kumar}
}
```

### APA Format
Satapathy, A. (2025). *The role of institutional quality in achieving SDGs in BRICS countries* [Bachelor's thesis, Indian Institute of Technology Kharagpur]. Supervised by Professor Mantu Kumar Mahalik.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Contact

**Archana Satapathy**  
Department of Mining Engineering  
Indian Institute of Technology Kharagpur  
Roll No: 21MI10012

**Supervisor: Professor Mantu Kumar Mahalik**  
Department of Humanities and Social Sciences  
Indian Institute of Technology Kharagpur

---

## 🙏 Acknowledgments

- Professor Mantu Kumar Mahalik for invaluable guidance
- Department of Humanities and Social Sciences, IIT Kharagpur
- World Bank for providing open-access data
- Sustainable Development Solutions Network for SDG Index data

## 📚 Related Publications

### Key References

1. **Acemoglu et al. (2001)** - The Colonial Origins of Comparative Development
2. **Kaufmann et al. (1999)** - Worldwide Governance Indicators
3. **Arellano & Bover (1995); Blundell & Bond (1998)** - System GMM Methodology
4. **Shahbaz et al. (2020)** - NARDL Models for BRICS Governance
5. **Sen (1999)** - Capability Approach Framework

Full bibliography available in [docs/report.pdf](docs/report.pdf)

---

**Last Updated**: October 2025  
**Status**: ✅ Research Complete | 📊 Analysis Validated | 📖 Documentation Complete
