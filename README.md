# Multi-Asset Tactical Overlay Research

### *When an Attractive Backtest Is Still the Wrong Rule to Trade*

> **A simple 6-month trend rule looked attractive in the historical record — even against a portfolio with the same average leverage. It still did not earn adoption.**
>
> The reason is the point of this project: a backtest can improve before the underlying policy becomes something worth trading.

## The question

The starting point is a strategic multi-asset portfolio: **30% U.S. stocks (VTI), 40% long-term U.S. Treasuries (TLT), 15% intermediate-term U.S. Treasuries (IEF), 7.5% broad commodities (DBC), and 7.5% gold (GLD)**.

The goal was not to optimize those weights. It was to ask a narrower practical question:

**Can simple tactical overlays — temporary changes around the strategic Core — improve the portfolio without turning it into a fragile, always-on, or implementation-heavy trading system?**

I tested rebalancing rules, standing cash reserves, drawdown and rebound responses, volatility controls, and trend-based leverage across **320 strategy-grid evaluations**, then applied additional attribution and implementation checks to the ideas that looked most promising.

## What changed the decision

| Stage | What the evidence said | Why it mattered |
| --- | --- | --- |
| **Most simple overlays disappointed** | Rebalancing variants, cash reserves, drawdown/rebound rules, and volatility controls did not produce a compelling tactical policy. | The project did not start with a preferred winner and back-fit the story around it. |
| **A broad 6-month trend rule stood out** | Historically, it improved return and risk-adjusted metrics in both the long-history proxy view and the ETF-era view. | This was strong enough to justify deeper testing rather than immediate rejection. |
| **It was not just “more leverage”** | The dynamic rule still looked better than holding the same average leverage continuously. | The attractive result could not be dismissed as leverage alone. |
| **But the strategy was usually leveraged** | The trend signal was active roughly **three-quarters of the time**. | That changed the strategy's identity: it behaved more like a leveraged Core that occasionally de-risked than an occasional tactical overlay. |
| **Making it genuinely selective broke the case** | **0 of 6** sparse, occasional-use redesigns passed the consistency screen. | The version that matched the intended use case did not retain the evidence needed for adoption. |

### **The backtest looked good. The policy case did not.**

The final research decision was therefore **not** to promote a tactical trigger into the operating portfolio policy. The strategic Core remains the anchor, with annual rebalancing used as a weight-maintenance convention rather than as a performance-maximizing rule.

## The research path

```text
Strategic multi-asset Core
        ↓
Rebalancing / cash / drawdown / rebound / volatility / trend candidates
        ↓
320 strategy-grid evaluations
        ↓
Broad trend rule stands out
        ↓
Same-average-leverage comparison survives
        ↓
Strategy identity changes: leveraged ~three-quarters of the time
        ↓
Redesign for genuinely occasional use
        ↓
0 / 6 sparse variants pass the consistency screen
        ↓
No tactical trigger earns adoption
```

## Read the full analysis

The executed notebook contains the complete research trail: successful and failed strategy families, saved tables and charts, matched-exposure attribution, uncertainty diagnostics, financing sensitivity, implementation boundaries, and the final decision logic.

### **[Open the executed research notebook →](./Portfolio_Tactical_Overlay_Analysis.ipynb)**

Two complementary real-data views are used:

- **Long-history proxy view (1993–2025):** extends the economic history through asset-class proxy returns.
- **ETF-era view (2010–2026):** uses investable ETF histories; primary cross-family comparisons end in December 2025, with 2026 shown only as an update sensitivity.

These views are complementary constructions, **not independent replications**.

## What this project is — and is not

This is a reproducible investment-research case study about **decision quality**, not a claim that a profitable trading strategy was discovered.

The strongest historical result is deliberately subjected to additional tests that could invalidate its practical use. The long-history view includes modeled proxy construction, financing sensitivity is a simplified implementation boundary rather than an observed leveraged-product cost, and no real-money leverage or product implementation is authorized by this research.

## Reproduce it locally

The notebook is self-contained and already includes all saved outputs. To reproduce them, run all cells from the repository root; every input is read through a relative path under `data/`.

Requirements: Python with NumPy, pandas, Matplotlib, IPython, and Jupyter support. No network access is required for execution.

Public inputs:

- `data/long_history_monthly_returns.csv`
- `data/etf_month_end_adjusted_close.csv`
- `data/three_month_treasury_rate.csv`

See [`DATA_NOTES.md`](./DATA_NOTES.md) for source and construction notes.
