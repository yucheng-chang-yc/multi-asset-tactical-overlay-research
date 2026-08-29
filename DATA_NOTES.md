# Data notes

## Files

- `data/long_history_monthly_returns.csv` contains monthly asset-class proxy returns used for the long-history view. Its ETF-style column names identify portfolio roles; they do not imply that each ETF existed throughout the history.
- `data/etf_month_end_adjusted_close.csv` contains month-end adjusted closes for VTI, TLT, IEF, DBC, and GLD. The notebook calculates monthly returns directly from these closes.
- `data/three_month_treasury_rate.csv` contains three-month Treasury-bill observations. The notebook converts the annual percentage rate to a monthly return and lags it by one month.

## Interpretation limits

The two data views are complementary constructions with substantial calendar overlap, not independent replications. Primary cross-family comparisons end in December 2025; the 2026 ETF-era observations are shown only as a labeled update sensitivity.

The long-history view includes modeled economic proxies. It is not actual ETF adjusted-close history and does not fully encode the upstream splice and calibration steps. Proxy histories can differ from live products because of fees, tracking, liquidity, taxes, financing, and product continuity. The notebook therefore treats implementation evidence and financing assumptions as explicit limitations.
