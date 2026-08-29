# Multi-Asset Tactical Overlay Research

### *When an Attractive Backtest Is Still the Wrong Rule to Trade*

> **A simple 6-month trend rule looked attractive in the historical record — even against a portfolio with the same average leverage. It still did not earn adoption.**
>
> The reason is the point of this project: a backtest can improve before the underlying policy becomes something worth trading.

## Starting from an All Weather idea

The appeal of an **All Weather-style** portfolio is simple: do not build the whole portfolio around one macro forecast. Combine assets that respond differently to surprises in economic growth and inflation, so the strategic Core has more than one source of resilience.

That makes it a useful starting point for a harder question:

**If the Core is already diversified across very different economic exposures, can a small set of simple tactical rules improve it further without turning it into an always-on trading system?**

For this research, I use a simplified ETF-based All Weather-style Core:

| Asset role | Weight | ETF used here |
| --- | ---: | --- |
| U.S. stocks | 30% | VTI |
| Long-term U.S. Treasuries | 40% | TLT |
| Intermediate-term U.S. Treasuries | 15% | IEF |
| Broad commodities | 7.5% | DBC |
| Gold | 7.5% | GLD |

This mix is used as the **strategic starting point**, not as something optimized inside this project. Background on the underlying idea: [Bridgewater — *The All Weather Story*](https://www.bridgewater.com/research-and-insights/the-all-weather-story).

## The tactical question

I tested rebalancing rules, standing cash reserves, drawdown and rebound responses, volatility controls, and trend-based leverage across **320 parameterized strategy-grid evaluations**, then applied additional attribution and implementation checks to the ideas that looked most promising. These grid rows are related configurations, not 320 independent statistical tests.

## What changed the decision

| Stage | What the evidence said | Why it mattered |
| --- | --- | --- |
| **Most simple overlays disappointed** | Rebalancing variants, cash reserves, drawdown/rebound rules, and volatility controls did not produce a compelling tactical policy. | The trend result emerged from a broader rule search rather than a single isolated backtest. |
| **A broad 6-month trend rule stood out** | Historically, it improved return and risk-adjusted metrics in both the long-history proxy view and the ETF-era view. | This was strong enough to justify deeper testing rather than immediate rejection. |
| **It was not just “more leverage”** | The dynamic rule still looked better than holding the same average leverage continuously. | The attractive result could not be dismissed as leverage alone. |
| **But the strategy was usually leveraged** | The trend signal was active roughly **three-quarters of the time**. | That changed the strategy's identity: it behaved more like a leveraged Core that occasionally de-risked than an occasional tactical overlay. |
| **Making it genuinely selective broke the case** | **0 of 6** sparse, occasional-use redesigns passed the consistency screen. | The version that matched the intended use case did not retain the evidence needed for adoption. |

### **The backtest looked good. The policy case did not.**

The final research decision was therefore **not** to promote a tactical trigger into the operating portfolio policy. The strategic Core remains the anchor, with annual rebalancing used as a weight-maintenance convention rather than as a performance-maximizing rule.

### **[Open the executed research notebook →](./Portfolio_Tactical_Overlay_Analysis.ipynb)**

The notebook contains the complete research trail: successful and failed strategy families, saved tables and charts, matched-exposure attribution, uncertainty diagnostics, financing sensitivity, implementation boundaries, and the final decision logic.

## Two complementary evidence views

- **Long-history proxy view (1993–2025):** extends the economic history through asset-class proxy returns.
- **ETF-era view (2010–2026):** uses investable ETF histories; primary cross-family comparisons end in December 2025, with 2026 shown only as an update sensitivity.

These views are complementary constructions, **not independent replications**.

## What this project is — and is not

This is a reproducible investment-research case study about **decision quality**, not a claim that a profitable trading strategy was discovered.

The ETF mix above is a simplified retail implementation inspired by All Weather principles, not a reconstruction of Bridgewater's institutional portfolio. The strongest historical result is deliberately subjected to additional tests that could invalidate its practical use. The long-history view includes modeled proxy construction, and financing sensitivity is a simplified implementation boundary rather than an observed leveraged-product cost. **This research does not recommend real-money leverage or validate a specific leveraged-product implementation.**

## Reproduce it locally

The notebook is self-contained and already includes all saved outputs. To reproduce them, run all cells from the repository root; every input is read through a relative path under `data/`.

Requirements: Python with NumPy, pandas, Matplotlib, IPython, and Jupyter support. No network access is required for execution.

Public inputs:

- `data/long_history_monthly_returns.csv`
- `data/etf_month_end_adjusted_close.csv`
- `data/three_month_treasury_rate.csv`

See [`DATA_NOTES.md`](./DATA_NOTES.md) for source and construction notes.
