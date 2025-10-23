Here’s an **extremely professional and publication-ready `README.md`** for your GitHub repository — written in a polished research + engineering tone that appeals to both finance professionals and data scientists. It includes structured sections, LaTeX-style math for equations, and strong readability for a GitHub audience.

---

````markdown
# 📈 How Bitcoin Shifts the Efficient Frontier  
*A Walk-Forward Multi-Objective Optimization Study in Python*

---

## 🧭 Overview

This project investigates whether adding **Bitcoin (BTC)** to a traditional **equity portfolio** improves **risk-adjusted performance** under *realistic market frictions*.  

Using a **walk-forward mean–variance optimization** framework, we explore how a capped BTC allocation affects the **out-of-sample efficient frontier**, accounting for practical constraints such as transaction costs, shrinkage, and rolling covariance estimation.

The results demonstrate that even a **small, capped BTC sleeve** (≤10%) can **shift the efficient frontier upward**, improving Sharpe and Calmar ratios while maintaining stable volatility.

---

## ⚙️ Methodology

The study employs a **walk-forward mean–variance optimizer** with:


- **Long-only constraints**: \( w \ge 0, \; \mathbf{1}^\top w = 1 \)
- **BTC allocation cap**: \( w_{\text{BTC}} \le 0.10 \)
- **EWMA covariance** with decay factor \( \lambda = 0.94 \)
- **Shrinkage** for both means and covariances
- **Rolling winsorization** to reduce tail risk
- **Turnover costs** of 10 basis points per round trip
- **Intersected trading-day calendar** for ETF + BTC synchronization

---

## 🧮 Mathematical Formulation

The scalarized mean–variance objective for a given \( \alpha \in [0,1] \) is:

$$
J_\alpha(w) = (1 - \alpha)\, w^\top \Sigma w - \alpha\, \mu^\top w
$$

subject to:

$$
w \ge 0, \quad \mathbf{1}^\top w = 1, \quad w_{\text{BTC}} \le 0.10
$$

Weights are updated using **projected gradient descent** with re-projection onto the simplex and optional capping.

---

## 🔁 Walk-Forward Optimization Procedure

1. **Estimate** parameters (μ, Σ) on a rolling window of `lookback_days = 63`.
2. **Hold** the optimized weights for `hold_days = 63` out-of-sample.
3. **Apply turnover cost** at each rebalance.
4. **Repeat** across all rolling windows and aggregate out-of-sample results.
5. **Compare** Stocks-only vs. Stocks+BTC portfolios across an α-grid.

---

## 📊 Key Results

At the same risk-aversion level \( (\alpha = 0.95) \):

| Portfolio        | Sharpe | Return | Volatility | Max DD | Calmar |
|------------------|:------:|:-------:|:------------:|:-------:|:-------:|
| Stocks-only      | 0.60   | 8.31%   | 13.93%       | −35.5%  | 0.23    |
| Stocks + BTC (10%) | **0.86** | **12.27%** | **14.34%** | −39.9%  | **0.31** |

Average realized BTC weight ≈ **5.8%**, never reaching the 10% cap — confirming that performance gains stem from **diversification**, not from concentrated exposure.

---

## 📈 Visual Highlights

- **Walk-Forward Efficient Frontier:** BTC curve consistently dominates the stocks-only curve.  
- **Cumulative Equity Growth:** BTC-enhanced portfolio exhibits higher long-term compounding.  
- **BTC Weight Path:** Average weight remains stable and below cap throughout the test period.

---

## 🧩 Interpretation

- BTC acted as a **decorrelated risk premium**, improving multi-asset efficiency.  
- The effect persisted even with realistic frictions (winsorization, turnover costs).  
- The improvement reflects **cross-asset diversification**, not speculative risk-taking.  

---

## 🧠 Future Extensions

Potential next steps for deeper analysis:

- **Cap sensitivity**: 5%, 10%, 20% BTC allocation tests  
- **Rebalance cadence**: monthly vs. quarterly  
- **Expanded universes**: add bonds, commodities, or gold  
- **Regime conditioning**: activate BTC only in risk-on environments  
- **Risk-target optimization**:  
  $$
  \min_{w} w^\top \Sigma w \quad \text{s.t. } \mu^\top w \ge R^*
  $$

---

## 🧰 Tech Stack

| Component | Description |
|------------|-------------|
| **Language** | Python 3.10+ |
| **Libraries** | `numpy`, `pandas`, `yfinance`, `matplotlib` |
| **Environment** | Google Colab / Jupyter Notebook |
| **Data Source** | Yahoo Finance (`BTC-USD`, `SPY`, `QQQ`, `VEU`, `IWM`) |

---
## 🏁 Conclusion

A **small, prudently capped BTC sleeve** enhanced the **out-of-sample efficient frontier** under realistic assumptions.
The improvement came not from leverage or speculation, but from **structural diversification** within a multi-asset framework.

BTC, when managed responsibly, can serve as a **constructive component** in a modern equity portfolio.

---

## 📚 Citation

If you use this project in research, please cite as:

> Khan, M. A. (2025). *How Bitcoin Shifts the Efficient Frontier: A Walk-Forward Multi-Objective Optimization Study in Python.*

---

## 🧾 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

---

*Author: [MD Amir Khan](https://github.com/Mkhan2317)*
*Affiliation: Stevens Institute of Technology – M.S. Financial Engineering*
*Contact: [mkhan37@stevens.edu](mkhan37@stevens.edu)*


