# Monte Carlo LBO & NPV Valuation | Enerpac Tool Group

**Python | Financial Modeling | Monte Carlo Simulation | Valuation**

## Overview

I created a Python-based Leveraged Buyout (LBO) model for Enerpac Tool Group utilizing historical financial information obtained from SEC filings. I used **10,000 Monte Carlo simulations** to assess potential investment returns, sponsor net present value (NPV), and acquisition price sensitivity to uncertainty in future operational performance and market conditions.

My goal was to identify the maximum acquisition valuation that would result in at least a **70% probability of achieving a minimum 20% annualized return**.

## Key Findings

| Metric | Result |
|---|---:|
| Deterministic Sponsor IRR | 15.95% |
| Deterministic Sponsor MOIC (9.0x entry) | 2.10x |
| Deterministic Sponsor NPV (20% Discount Rate) | -$124.76M |
| Median Simulated IRR (5th–95th percentile) | 15.8% (5.4% to 25.1%) |
| Mean Simulated NPV (20% Discount Rate) | -$118.76M |
| Median Simulated NPV (5th–95th percentile) | -$130.36M (-$377.32M to +$183.74M) |
| Probability of Positive NPV | 22.83% |
| Probability of Negative IRR | 0.67% |
| Scenarios Requiring Follow-on Sponsor Equity | 0% |
| Maximum Entry EV/EBITDA Multiple @ 70% Probability | **7.56x** |
| Implied Maximum Enterprise Value | **$1.11B** |

*All results were derived from hypothetical transaction assumptions and standalone FY2026 financials.*

*Simulated IRR and NPV figures are measured at a 9.0x entry multiple. Because NPV is discounted at the 20% hurdle rate, the probability of positive NPV is the same as the probability of an IRR of at least 20%.*

### Interpretation

At a 9.0x entry, the deal reaches a 20% IRR in fewer than one in four scenarios. The downside is limited, though: under 1% of scenarios lose capital, and no simulated path required additional sponsor equity. To clear the hurdle with 70% confidence, a sponsor could pay at most 7.56x FY2026 EBITDA (about $1.11B). Enerpac's public enterprise value was roughly $1.9–2.0B during 2026. So under these assumptions, a take-private targeting a 20% return does not work at market prices. The constraint is the hurdle rate relative to the price, not the business's cash generation.

### Sensitivity

| Exit-Multiple Volatility (× base SD) | P(IRR ≥ 20%) at 9.0x | Median IRR | 5th Percentile IRR |
|---|---:|---:|---:|
| 0.75x | 20.36% | 15.80% | 6.82% |
| 1.00x (base) | 22.83% | 15.76% | 5.43% |
| 1.25x | 25.00% | 15.71% | 3.83% |

Widening exit-multiple uncertainty *raises* the hit rate because the base case sits below the hurdle, so more spread pushes more scenarios over 20%, while the downside tail worsens. The price frontier is steep near the answer: the probability of success falls from 71.9% at 7.5x to 54.4% at 8.0x.

## Methodology

- **Financial Modeling:** Historical FY2021–FY2026 SEC financial data was extracted and used to build a five-year LBO including debt amortization, cash flow forecasting, and sponsor equity returns.
- **Monte Carlo Simulation:** Correlated uncertainty in revenue growth, EBITDA margin, interest rate, and exit valuation was modeled through 10,000 simulations.
- **NPV Analysis:** Simulated sponsor cash flows were discounted at a 20% required return to calculate the distribution and probability of positive NPV.
- **Valuation Optimization:** The maximum entry EV/EBITDA multiple satisfying the required return probability was calculated.
- **Model Validation:** Automated checks for financial reconciliation, simulation outputs, and valuation consistency were implemented.
- **Data Provenance:** Every SEC figure is stored with its XBRL tag, accession number and filing date (`sec_provenance.csv`), and the model stops rather than filling in missing values.
- **Simulation Design:** Each scenario combines four correlated scenario-level factors with year-specific shocks (70% systematic / 30% idiosyncratic), so growth, margin and rates vary year by year. The random seed is fixed (20261114), and the same 10,000 paths are reused at every entry price so price comparisons are not distorted by sampling noise.
- **Exact Price Solve:** Because the entry price only changes the upfront equity check, not operating cash flows, the maximum affordable multiple is solved algebraically for each scenario. The 7.56x answer is the exact 70th-percentile cutoff across the 10,000 scenarios, with no interpolation.
- **Cross-checks:** Flat simulation paths reproduce the deterministic model exactly, sources equal uses, the price frontier is non-increasing, NPV matches `numpy_financial.npv` on sampled scenarios, and NPV and IRR success rates agree.

## Key Assumptions

| Assumption | Value |
|---|---:|
| FY2026 revenue / EBITDA (unadjusted) | $652.3M / $146.7M |
| Entry and exit multiple (base) | 9.0x |
| Debt at close | 4.0x EBITDA ($586.8M) |
| Interest rate (base) | 8.5% |
| Transaction / financing fees | 2% of EV / 2% of debt |
| Mandatory amortization / cash sweep | 5% of original debt per year / 100% |
| Cash tax rate | 25% |
| Minimum operating cash | $20M |
| Revenue growth (mean, SD) | 5.0%, 2.5% |
| Annual EBITDA margin change (mean, SD) | +0.2 pts, 0.3 pts |
| Exit multiple (mean, SD, bounds) | 9.0x, 1.25x, 5.0x–13.0x |
| Interest rate (SD, bounds) | 1.5%, 4%–15% |
| Hold period | 5 years |

## Visualizations

The notebook contains distributions of simulated IRR and NPV, an exit valuation sensitivity chart, and an acquisition price feasibility curve.

- `01_irr_distribution.png`: simulated sponsor IRR against the 20% target and the deterministic base
- `02_exit_multiple_vs_irr.png`: exit EV/EBITDA versus sponsor IRR for each scenario
- `03_price_feasibility.png`: probability of a 20% IRR across entry multiples from 4.0x to 12.0x
- `04_monte_carlo_npv_distribution.png`: simulated sponsor NPV against zero NPV and the base case

## Limitations

- EBITDA is unadjusted (operating income + D&A), so multiples are not directly comparable to the adjusted EBITDA multiples in company and market reporting.
- Simulation distributions and correlations are analyst assumptions, not estimates from historical data.
- Acquired target cash is treated as a funding source, which a real transaction would need to confirm.
- There is no revolver, no tax loss carryforward and no exit transaction costs. The sponsor is assumed able to fund any capital call.
- The analysis is standalone and excludes the SFE acquisition.

## Tools

**Python:** NumPy, pandas, Matplotlib, NumPy Financial, Requests

**Data:** SEC EDGAR Company Facts API

**Environment:** Google Colab / Jupyter Notebook

---

*This project is an independent educational valuation exercise. All financial projections, financing terms, and simulation distributions are illustrative and do not constitute investment advice.*
