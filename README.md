# Quantitative Portfolio Analysis: Football Clubs & Solana
*This R project evaluates the risk-adjusted performance of football club equities and cryptocurrency.*

[**Report (PDF – online)**](https://drive.google.com/file/d/1PhT8aecdhZV8dT5PVNbNAhvdVucygpIk/view?usp=drive_link)

---

## 🎯 Overview
This project applies Modern Portfolio Theory to assess the risk-adjusted performance and diversification benefits of European football club stocks combined with the Solana cryptocurrency.

**Objectives**
- Analyze return and volatility of football clubs and Solana (2023-2024)
- Assess performance using risk-adjusted indicators (Sharpe, Jensen, Treynor, Sortino, Roy, Information ratio)
- Construct efficient minimum variance and tangency portfolios using Modern Portfolio Theory
- Visualize correlations, covariances, and efficient frontiers

---

## 🗄️ Data
- **Source:** Yahoo Finance (JUVE.MI, SSL.MI, XXT.SG, CCP.L, BVB.MU, SCP.LS, AAB.CO, GSRAY.IS, AJAX.AS, SOL-USD)
- **Time Period / Size:** 2023-12-01 to 2024-11-30, daily frequency
- **Target Variable:** Asset closing prices and daily returns
- **Data Availability:** Publicly available via API

---

## 🧠 Methodology
- **Theoretical Approach:** Modern Portfolio Theory (Markowitz)
- **Mathematical Framework:** Variance-covariance matrix optimization, GARCH models for conditional volatility
- **Evaluation Strategy:** Risk-adjusted performance metrics comparison

---

## ⚙️ Features
- **Retrieve Financial Data:** Extract daily asset prices automatically from Yahoo Finance
- **Calculate Return Metrics:** Compute daily returns, volatilities, and descriptive statistics
- **Visualize Price Dynamics:** Generate time series plots for individual prices and returns
- **Compute Covariance Matrices:** Estimate variance-covariance and correlation matrices across assets
- **Optimize Risk-Return:** Implement minimum variance and tangent portfolios
- **Plot Efficient Frontier:** Map the risk-return optimization boundary graphically

---

## 🧰 Tech Stack
- **Language:** R
- **Numerical Computing & Data Manipulation:** tidyverse, xts, data.table
- **Econometrics & Statistical Inference:** tseries
- **Time Series Analysis:** rugarch
- **Quantitative Finance:** tidyquant, PerformanceAnalytics
- **Data Visualization:** ggplot2, patchwork, corrplot
- **Reporting & Documentation:** Quarto

---

## 📦 Installation

```bash
git clone https://github.com/floriancrochet/master-year1-financial-asset-valuation.git
cd master-year1-financial-asset-valuation
Rscript -e 'install.packages(c("tidyquant", "tidyverse", "tseries", "rugarch", "patchwork", "corrplot", "xts", "PerformanceAnalytics", "data.table"))'
```

---

## 💻 Usage Example

### Reproducing the Analysis / Execution Pipeline

```r
library(tidyverse)
library(tidyquant)

# Load data from Yahoo Finance
tickers <- c("JUVE.MI", "SSL.MI", "XXT.SG", "CCP.L", "BVB.MU",
             "SCP.LS", "AAB.CO", "GSRAY.IS", "AJAX.AS", "SOL-USD")
data <- map(tickers, function(i) tq_get(i, from = "2023-12-01", to = "2024-11-30"))

# Compute returns
base <- bind_rows(data) |>
  group_by(symbol) |>
  mutate(return = close / lag(close) - 1)

# Plot asset returns
base |>
  ggplot(aes(x = date, y = return, color = symbol)) +
  geom_line() +
  labs(title = "Asset Returns Over Time")
```

---

## 📂 Project Structure

```text
master-year1-financial-asset-valuation/
│
├── report/
│   └── report.pdf
├── .gitignore
├── LICENSE
├── README.md
├── master-year1-financial-asset-valuation.Rproj
└── project.qmd
```

---

## 📈 Results

### Key Findings
- **Volatility Divergence:** Solana (SOL-USD) exhibits extremely high volatility and kurtosis, confirming its speculative nature, while football clubs show moderate volatility and similar sectoral correlations.
- **Portfolio Efficiency:** The minimum variance portfolio offers a lower risk (σ = 0.0115) and slightly higher expected return than the tangent portfolio.
- **Diversification:** Diversification significantly improves efficiency, confirming the theoretical expectations of Markowitz's Modern Portfolio Theory.

---

## 📚 References
- Hyndman & Athanasopoulos, *Forecasting: Principles and Practice*
- Markowitz, *Portfolio Selection*
- Sharpe, *Capital Asset Prices: A Theory of Market Equilibrium*

---

## 📜 License
This project is released under the MIT License.
© 2025 Pierre Quintin de Kercadio and Florian Crochet

---

## 👤 Authors
**Pierre Quintin de Kercadio**
[GitHub Profile](https://github.com/PierreQDK)

**Florian Crochet**
[GitHub Profile](https://github.com/floriancrochet)

*Master 1 – Econometrics & Statistics, Applied Econometrics Track*

---

## 🤝 Acknowledgments
This work was conducted as part of the M1 Econometrics and Statistics – Applied Econometrics (ECAP) course.
