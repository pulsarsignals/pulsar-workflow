# Reports — how these numbers are produced

This directory holds the machine-generated signal backtest reports. Every figure is reproducible
from the price database and the indicator definitions in [`../docs/indicator-reference.md`](../docs/indicator-reference.md).

## What is here

| File | Contents |
|---|---|
| `YYYY-MM-signal-backtest.md` | The monthly report: eight conventional signals at 5, 10 and 20 trading-day horizons |
| `index.md` | Auto-updated index of all monthly reports |
| `../data/signal-results-YYYY-MM.csv` | The same results as machine-readable data (one row per signal × horizon) |

The one-off [`2026-technical-signal-report.md`](2026-technical-signal-report.md) is a long-form write-up
of the same dataset, with narrative, interpretation and a full list of limitations.

## Update schedule

The reports are regenerated automatically after the weekly backtest run:

```
Monday 07:30   backtest_engine.py        re-run the market-wide backtest
Monday 09:00   gen_github_report.py      regenerate report + CSV + index
               github_push.py            push to GitHub (only changed files)
```

A report is only rewritten when the underlying backtest data changes, so a quiet week produces no
commit rather than an empty one.

## Signals tested

All parameters are conventional and fixed. Nothing is tuned against the results.

| Signal | Definition |
|---|---|
| RSI oversold recovery | RSI(14) crosses up through 30 |
| RSI overbought reversal | RSI(14) crosses down through 70 |
| MACD golden cross | MACD(12,26,9) line crosses above its signal line |
| MACD death cross | MACD line crosses below its signal line |
| MA20/60 golden cross | SMA(20) crosses above SMA(60) |
| MA20/60 death cross | SMA(20) crosses below SMA(60) |
| Combined bullish setup | MACD golden cross AND RSI < 50 AND price > SMA(20) |
| Combined bearish setup | MACD death cross AND RSI > 50 AND price < SMA(20) |

## Statistics — and why the median leads

For each signal and horizon the report gives the occurrence count, win rate, **median**, a
**1%-trimmed mean**, the quartiles, and the raw arithmetic mean.

The median is the primary statistic because a cross-section of several thousand stocks, many of them
small caps, contains extreme outliers. For one RSI-oversold row the arithmetic mean 20-day return is
**+43.8%** while the median is **+0.79%** — the mean is dominated by a handful of split-adjusted
data artefacts, not by the typical trade. The trimmed mean (which discards the top and bottom 1%)
sits close to the median and is the second statistic we trust.

## Known data artefacts in the `best_pct` / `worst_pct` columns

The CSV reports the single best and worst observed forward return for each signal. In some rows these
reach implausible magnitudes (e.g. `+1449900%`, `−99.998%`). These are **not** real tradeable outcomes.
They are artefacts of split/dividend adjustment applied across a thin or interrupted price history, or
of a corporate action that the adjustment process could not resolve cleanly. Roughly 0.2–1.3% of rows
in the affected signals are such outliers.

We publish them rather than silently clip them, but they should not be read as returns anyone could
earn. The median and trimmed mean are specifically chosen to be robust to exactly this tail.

## Limitations (read before citing)

1. The sample spans roughly two years and does not cover a full bull/bear cycle.
2. Returns are **gross** — no commission, spread or slippage. At a 0.1% round trip most medians fall to zero or below.
3. Exits are time-based only; no stop-loss or take-profit.
4. Illiquid small caps are over-represented and could not realistically be filled at the closing print.
5. Parameters are conventional but arbitrary.
6. No survivorship correction for delisted names.
7. Returns are **absolute, not excess** over a market benchmark — a positive median may simply reflect the market rising.

**This is descriptive statistics, not a forecast, a strategy, or investment advice.**
