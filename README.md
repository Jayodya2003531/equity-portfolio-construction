# equity-portfolio-construction & Monte Carlo Simulation
10-stock S&amp;P 500 equity portfolio | Minimum Volatility · Monte Carlo · Efficient Frontier | Data: investing.com 2023–2026
# 📈 Equity Portfolio Construction & Monte Carlo Simulation

> **10-Stock S&P 500 Portfolio** | Historical Data: Jan 2023 – Jan 2026 | Source: investing.com

---

## 🧭 Project Overview

This project constructs and analyses an **equity portfolio of 10 major S&P 500 stocks** using quantitative methods in both Python and Microsoft Excel. It covers two core activities in modern portfolio theory:

| Activity | Description |
|---|---|
| **Activity 1** | Minimum Volatility Portfolio construction · Monte Carlo simulation (5,000 paths) · Correlation matrix comparison · Portfolio return distribution |
| **Activity 2** | Efficient Frontier construction with the Minimum Volatility Portfolio highlighted |

---

## 🏦 Stock Universe

Historical daily closing prices sourced from **[investing.com](https://www.investing.com)** covering **January 2023 – January 2026** (752 trading days).

| # | Stock | Ticker | Sector | Ann. Return | Ann. Volatility | Sharpe |
|---|---|---|---|---|---|---|
| 1 | NVIDIA | NVDA | Technology | 68.93% | 48.37% | 1.43 |
| 2 | Apple | AAPL | Technology | 18.53% | 25.67% | 0.72 |
| 3 | Amazon | AMZN | Consumer Discretionary | 29.78% | 30.96% | 0.96 |
| 4 | Alphabet | GOOGL | Communication Services | 41.61% | 29.55% | 1.41 |
| 5 | Meta | META | Communication Services | 31.82% | 35.64% | 0.89 |
| 6 | Johnson & Johnson | JNJ | Healthcare | 12.33% | 17.24% | 0.72 |
| 7 | JPMorgan Chase | JPM | Financials | 26.76% | 22.78% | 1.18 |
| 8 | Coca-Cola | KO | Consumer Staples | 7.63% | 15.41% | 0.50 |
| 9 | ExxonMobil | XOM | Energy | 12.30% | 22.98% | 0.54 |
| 10 | Procter & Gamble | PG | Consumer Staples | −3.10% | 17.22% | −0.18 |

> Returns and volatilities are annualised from daily log returns. Risk-free rate = 0%.

---

## 🏆 Activity 1 — Minimum Volatility Portfolio

### Optimal Weights (SLSQP Optimization, Long-Only)

| Stock | Weight | Role in Portfolio |
|---|---|---|
| 🥤 Coca-Cola | **26.11%** | Low volatility anchor |
| 💊 J&J | **23.24%** | Defensive healthcare |
| 🧴 P&G | **14.59%** | Defensive consumer staple |
| ⛽ ExxonMobil | **13.73%** | Diversifier (low correlation) |
| 🔍 Alphabet | 6.00% | Growth with moderate vol |
| 🏦 JPMorgan | 4.59% | Financial exposure |
| 💚 NVIDIA | 5.36% | Small high-growth allocation |
| 📦 Amazon | 4.37% | Small growth allocation |
| 👍 Meta | 2.00% | Minimal high-vol exposure |
| 🍎 Apple | ~0.00% | Excluded by optimizer |
<img width="752" height="452" alt="image" src="https://github.com/user-attachments/assets/057a00b5-9291-4b96-9c9c-e0fc1e3a38de" />


### Portfolio Performance

| Metric | Value |
|---|---|
| **Annual Return** | **15.04%** |
| **Annual Volatility** | **10.25%** |
| **Sharpe Ratio** | **1.467** |
| Daily Return (mean) | 0.0597% |
| Daily Volatility | 0.6454% |

> The optimizer concentrates weight in **defensive, low-volatility** stocks (Coca-Cola, J&J, P&G, Exxon) while keeping small allocations in high-growth names (NVIDIA, Alphabet) for return enhancement.

---

## 🎲 Monte Carlo Simulation (5,000 Paths)

Correlated price paths were generated using **Cholesky decomposition** of the historical covariance matrix, preserving the full inter-stock correlation structure.




### Simulation Results

| Metric | Value |
|---|---|
| Simulated Mean Daily Return | 0.0579% |
| Simulated Daily Std Dev | 0.6512% |
| Skewness | Near-zero (symmetric) |
| **VaR (5%, 1-day)** | **−1.00%** |
| CVaR (Expected Shortfall) | −1.28% |
| Correlation Matrix R² | **0.9997** (simulated vs market) |

> The simulated correlation matrix achieves R² = 0.9997 against the market correlation matrix — confirming the Cholesky method accurately replicates real-world stock dependencies.
<img width="752" height="447" alt="image" src="https://github.com/user-attachments/assets/2096c226-ba54-4a49-bfae-52344924dc78" />
<img width="858" height="448" alt="image" src="https://github.com/user-attachments/assets/0db83ec9-dc3c-455a-ab40-666d997ff709" />


---

## 📉 Activity 2 — Efficient Frontier

<img width="859" height="442" alt="image" src="https://github.com/user-attachments/assets/454a0524-0b9f-4323-8a6e-63b53c1ad54b" />


The frontier was constructed by solving **300 constrained minimum-variance optimizations** across a spectrum of target returns. Each point represents the lowest possible volatility achievable for a given return level.

**Key observations:**
- The **Minimum Volatility Portfolio ★** sits at the leftmost point of the frontier
- Defensive stocks (KO, JNJ, PG) dominate at the low-volatility end
- NVIDIA and Alphabet gain weight as target return increases along the frontier
- The Capital Allocation Line (Sharpe = 1.467) is plotted from the Min-Vol point

---

## 🛠️ Tools & Technologies

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?logo=microsoft-excel&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?logo=scipy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?logoColor=white)

| Tool | Purpose |
|---|---|
| **Python / NumPy** | Matrix operations, Cholesky decomposition, optimization |
| **SciPy (SLSQP)** | Constrained quadratic portfolio optimization |
| **Pandas** | Data cleaning and return calculations |
| **Matplotlib** | Visualization (heatmaps, histograms, frontier plot) |
| **Microsoft Excel + Solver** | Manual portfolio construction & Efficient Frontier |
| **openpyxl** | Automated Excel report generation |
| **investing.com** | Historical stock price data source |

---

## 🚀 How to Run

### 1. Clone the repo
```bash
git clone https://github.com/YOUR_USERNAME/portfolio-optimization-analysis.git
cd portfolio-optimization-analysis
```

### 2. Install dependencies
```bash
pip install numpy pandas scipy matplotlib openpyxl
```

### 3. Run the analysis
```bash
python code/portfolio_analysis.py
```

Outputs (charts + Excel report) will be saved to the `outputs/` folder.

---

## 📁 Repository Structure

```
portfolio-optimization-analysis/
│
├── 📁 data/
│   └── A3_s17349.xlsx           # Raw stock price data (investing.com)
│
├── 📁 outputs/
│   ├── CS2-s17349.xlsx          # Full formatted Excel report
│   ├── activity1.png            # Monte Carlo charts
│   └── activity2.png            # Efficient Frontier chart
│
├── 📁 code/
│   └── portfolio_analysis.py    # Full Python analysis script
│
├── 📁 images/                   # Charts for README display
│   ├── activity1.png
│   └── activity2.png
│
└── README.md
```

---

## 📚 Methodology Notes

- **Returns:** Daily log returns — `ln(Pₜ / Pₜ₋₁)`
- **Covariance:** Sample covariance matrix (N−1 denominator)
- **Optimization:** Long-only (wᵢ ≥ 0), fully invested (Σwᵢ = 1), SLSQP solver
- **Monte Carlo:** Cholesky-correlated normal draws · S₁ = S₀ · exp(μ + Lz)
- **Frontier:** 300 target return levels, each solved independently
- **Annualisation:** Returns × 252, Volatility × √252

---


---

*Data source: [investing.com](https://www.investing.com) · Period: Jan 2023 – Jan 2026 · 752 trading days*
