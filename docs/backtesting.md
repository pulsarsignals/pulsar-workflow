# Signal Backtesting

**On the site:** `/backtest.php`

Most sites that publish technical signals do not say how often those signals worked. PulsarSignals runs
a market-wide backtest and publishes the full result set, including the findings that are not flattering.

---

## 1. What is tested

| Item | Value |
|---|---|
| Universe | ~6,800 US equities with at least 250 daily bars |
| Sample period | January 2024 to the latest close |
| Daily bars | ~3.88 million, split-adjusted closes |
| Holding periods | 5, 10 and 20 trading days |
| Entry / exit | Signal-day close / close after the holding period |
| Parameter tuning | None — conventional periods only |

Eight signals are tested: RSI oversold recovery, RSI overbought reversal, MACD golden cross, MACD
death cross, MA20/60 golden cross, MA20/60 death cross, a combined bullish setup, and a combined
bearish setup. Definitions are in the [Indicator reference](indicator-reference.md).

---

## 2. Statistical treatment

Small-cap price history contains extreme outcomes — very large gains and delistings to zero. An
arithmetic mean is dominated by those cases. Every published statistic therefore leads with:

- the **median** forward return
- a **1%-trimmed mean**
- the **win rate** (share of occurrences with a positive forward return)
- the 25th and 75th percentiles, and the best / worst outcomes

The raw mean is included only for transparency. Indicator calculations are implemented in pure numpy
and cross-checked against a reference implementation (maximum deviation under 0.0002).

---

## 3. How to read the results

Results are presented as a table of signal × horizon, plus a per-symbol view on company and comparison
pages. A representative extract at the 20-day horizon:

| Signal | Occurrences | Win rate | Median return |
|---|---|---|---|
| MACD death cross | 144,908 | 53.6% | +0.45% |
| RSI oversold recovery | 43,429 | 54.1% | +0.79% |
| MACD golden cross | 144,800 | 50.6% | +0.09% |
| MA20/60 golden cross | 31,391 | 48.8% | −0.04% |
| Combined bullish setup | 7,763 | 49.0% | −0.05% |

Numbers that do not support a strong claim are published rather than omitted. The site does not derive
a "recommended strategy" from these results.

---

## 4. Per-symbol statistics

The same signal definitions are applied to each symbol individually and stored as per-symbol
statistics: event count, win rate, median, mean, best and worst forward return, at each horizon.
Company pages show the full table for that ticker; comparison pages place two symbols' win rates side
by side. Occurrence counts are always shown so that small samples are not over-interpreted.

---

## 5. Limitations

1. The sample is roughly two years and does not span a full market cycle.
2. Returns are **gross** — commission, spread and slippage are not deducted. At a typical 0.1% round
   trip, most median returns here fall to zero or below.
3. Exits are time-based only; no stop-loss or take-profit rules are applied.
4. Small, illiquid names are over-represented and could not realistically be filled at the closing
   print.
5. Signal parameters are conventional but arbitrary; other periods give different results.
6. No survivorship correction is applied for delisted names.
7. Results are **absolute** returns, not excess returns against a market benchmark. A positive median
   return may partly reflect the market rising during the sample.
8. No per-stock data is published as part of the backtest dataset.

---

## 6. Reproduction

The backtest is deterministic given the same price history. Indicator formulas, signal definitions and
the statistical treatment are documented in the [Indicator reference](indicator-reference.md) and on
the site's `/methodology.php` page.

---

## Notes

These are descriptive statistics about past price behaviour. They are not forecasts, not a trading
strategy, and not investment advice. Past results do not imply future performance.
