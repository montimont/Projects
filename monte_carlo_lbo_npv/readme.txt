# Monte Carlo LBO & NPV Valuation | Enerpac Tool Group

**Python | Financial Modeling | Monte Carlo Simulation | Valuation**

## Overview

We created a Python-based Leveraged Buyout (LBO) model for Enerpac Tool Group utilizing historical financial information obtained from SEC filings. We used **10,000 Monte Carlo simulations** to assess potential investment returns, sponsor net present value (NPV), and acquisition price sensitivity to uncertainty in future operational performance and market conditions.

Our goal was to identify the maximum acquisition valuation that would result in at least a **70% probability of achieving a minimum 20% annualized return**.

## Key Findings

| Metric | Result |
|---|---:|
| Deterministic Sponsor IRR | 15.95% |
| Mean Simulated NPV (20% Discount Rate) | -$118.76M |
| Probability of Positive NPV | 22.83% |
| Maximum Entry EV/EBITDA Multiple @ 70% Probability | **7.56x** |
| Implied Maximum Enterprise Value | **$1.11B** |

*All results were derived from hypothetical transaction assumptions and standalone FY2026 financials.*

## Methodology

- **Financial Modeling:** Historical FY2021–FY2026 SEC financial data was extracted and used to build a five-year LBO including debt amortization, cash flow forecasting, and sponsor equity returns.
- **Monte Carlo Simulation:** Correlated uncertainty in revenue growth, EBITDA margin, interest rate, and exit valuation was modeled through 10,000 simulations.
- **NPV Analysis:** Simulated sponsor cash flows were discounted at a 20% required return to calculate the distribution and probability of positive NPV.
- **Valuation Optimization:** The maximum entry EV/EBITDA multiple satisfying the required return probability was calculated.
- **Model Validation:** Automated checks for financial reconciliation, simulation outputs, and valuation consistency were implemented.

## Visualizations

The notebook contains distributions of simulated IRR and NPV, an exit valuation sensitivity chart, and an acquisition price feasibility curve.

## Tools

**Python:** NumPy, pandas, Matplotlib, NumPy Financial, Requests

**Data:** SEC EDGAR Company Facts API

**Environment:** Google Colab / Jupyter Notebook

---

*This project is an independent educational valuation exercise. All financial projections, financing terms, and simulation distributions are illustrative and do not constitute investment advice.*
