# Financial Asset Evaluation  
*A quantitative analysis of football club equities and cryptocurrency performance.*

---

## 📘 Overview
This project analyzes and evaluates **ten financial assets**, including **nine publicly traded football clubs** and **one cryptocurrency (Solana)**, over the period from **December 2023 to November 2024**.  
It was developed as part of the **Master 1 – Econometrics and Statistics (Applied Econometrics)** program.

**Objectives**
- Examine return and volatility behavior of football club equities versus cryptocurrency  
- Assess performance using multiple **risk-adjusted indicators** (Sharpe, Jensen, Treynor, Sortino, Roy, Information ratio)  
- Apply **Modern Portfolio Theory** to construct **efficient portfolios** (minimum variance and tangency)  
- Visualize and interpret correlations, covariances, and efficient frontiers  

---

## ⚙️ Features
- Automated data retrieval from **Yahoo Finance**  
- Calculation of **daily returns, volatilities, and descriptive statistics**  
- Visualization of **price and return dynamics** per asset  
- Computation of **variance–covariance and correlation matrices**  
- Implementation of **risk–return optimization** (minimum variance and tangent portfolios)  
- Graphical representation of the **efficient frontier**

---

## 🧰 Tech Stack
**Language:** R  
**Libraries:** tidyquant, tidyverse, tseries, rugarch, patchwork, corrplot, xts, PerformanceAnalytics, ggplot2  

---

## ⚙️ Installation
Clone the repository and install dependencies:

```bash
git clone https://github.com/<your-username>/financial-asset-evaluation.git
cd financial-asset-evaluation
# Open the R project or .Rmd file in RStudio
```

> Ensure the listed R libraries are installed before running the analysis.

---

## 📚 Usage Example

```r
# Load data from Yahoo Finance
tickers <- c("JUVE.MI", "SSL.MI", "XXT.SG", "CCP.L", "BVB.MU",
             "SCP.LS", "AAB.CO", "GSRAY.IS", "AJAX.AS", "SOL-USD")
data <- map(tickers, function(i) tq_get(i, from = "2023-12-01", to = "2024-11-30"))

# Compute returns
base <- bind_rows(data) |>
  group_by(symbol) |>
  mutate(return = close / lag(close) - 1)

# Efficient frontier plot
ggplot(Actifs3bis, aes(x = Sdp, y = Ep)) +
  geom_point() + labs(title = "Efficient Frontier")
```

---

## 📂 Project Structure

```
financial-asset-evaluation/
│
├── data/               # Raw and cleaned financial data
├── src/                # R scripts and helper functions
├── notebooks/          # RMarkdown analyses
├── figures/            # Generated visualizations
├── results/            # Output tables and computed metrics
└── README.md
```

---

## 📊 Results
The analysis reveals:
- **Solana (SOL-USD)** exhibits extremely high volatility and kurtosis, confirming its speculative nature.  
- **Football clubs** show **moderate volatility** and similar sectoral correlations.  
- **Minimum variance portfolio** offers a lower risk (σ = 0.01148) and slightly higher expected return than the tangent portfolio.  
- **Diversification** significantly improves efficiency, confirming the theoretical expectations of **Markowitz’s Modern Portfolio Theory**.

![Efficient Frontier Example](./assets/efficient_frontier.png)

---

## 🧠 References
- Yahoo Finance (data source for all assets)  
  - [JUVE.MI](https://fr.finance.yahoo.com/quote/JUVE.MI/)  
  - [SSL.MI](https://fr.finance.yahoo.com/quote/SSL.MI/)  
  - [XXT.SG](https://fr.finance.yahoo.com/quote/XXT.SG/)  
  - [CCP.L](https://fr.finance.yahoo.com/quote/CCP.L/)  
  - [BVB.MU](https://fr.finance.yahoo.com/quote/BVB.MU/)  
  - [SCP.LS](https://fr.finance.yahoo.com/quote/SCP.LS/)  
  - [AAB.CO](https://fr.finance.yahoo.com/quote/AAB.CO/)  
  - [GSRAY.IS](https://fr.finance.yahoo.com/quote/GSRAY.IS/)  
  - [AJAX.AS](https://fr.finance.yahoo.com/quote/AJAX.AS/)  
  - [SOL-USD](https://fr.finance.yahoo.com/quote/SOL-USD/)  

> Additional academic references  
> - Markowitz, *Portfolio Selection*  
> - Sharpe, *Capital Asset Prices: A Theory of Market Equilibrium*  
> - Hyndman & Athanasopoulos, *Forecasting: Principles and Practice*  

---

## 📜 License
This project is released under the **MIT License**.  
© 2025 Pierre Quintin de Kercadio and Florian Crochet 

---

## 👤 Authors
**Pierre Quintin de Kercadio**  
[GitHub Profile](https://github.com/PierreQDK)  

**Florian Crochet**  
[GitHub Profile](https://github.com/floriancrochet)

*Master 1 – Econometrics & Statistics, Applied Econometrics Track*

---

## 💬 Acknowledgments
Conducted under the **M1 Econometrics and Statistics – Applied Econometrics (ECAP)** program.  
Special thanks to the open-source R community and academic contributors who supported this analysis.
