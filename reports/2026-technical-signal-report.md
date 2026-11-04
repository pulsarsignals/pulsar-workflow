# The 2026 Technical Signal Report

**What 3.88 million daily bars say about RSI, MACD and moving-average crosses**

Published by [PulsarSignals](https://pulsarsignals.com) · Data through November 2026

---

## Why this report exists

Technical analysis is taught through rules that are rarely tested on the instrument you are actually
trading. "Buy the golden cross" is stated as a fact on thousands of pages; almost none of them say what
happened afterwards, across how many occurrences, or on which stocks.

This report tests eight conventional signals on **6,867 U.S. equities** and **3,876,380 daily bars**
from January 2024 onward, and publishes the full result set — including the findings that do not
support the signals.

All figures are reproducible. Indicator math is implemented in pure numpy and cross-validated against
TA-Lib (maximum deviation < 0.0002 on 11,566 bars).

---

## Headline findings

### 1. The golden cross is not a reliable entry signal

The MA20/MA60 golden cross — probably the most widely recommended entry signal in retail technical
analysis — produced a **48.8% win rate** at a 20-trading-day horizon across 31,391 occurrences.
The median forward return was **−0.04%**.

| Horizon | Occurrences | Win rate | Median return | Trimmed mean |
|---|---:|---:|---:|---:|
| 5 days | 31,993 | 46.8% | −0.12% | −0.35% |
| 10 days | 31,763 | 47.5% | — | — |
| 20 days | 31,391 | **48.8%** | **−0.04%** | −0.07% |

### 2. The death cross was followed by positive returns

The MACD death cross — conventionally a sell signal — had a **53.6% win rate** and a **+0.45%** median
20-day forward return across 144,908 occurrences. Acting on it as an exit signal would have
systematically cut positions before further gains.

### 3. Adding filters did not help

A combined bullish setup (MACD golden cross + RSI below 50 + price above MA20) reduced the sample from
~145,000 to 7,763 occurrences without improving the outcome: **49.0% win rate, −0.05% median**.

### 4. RSI oversold was the strongest of the eight — and still small

RSI oversold recovery: **54.1% win rate, +0.79% median** across 43,429 occurrences. With a 0.1%
round-trip cost, most of that disappears.

---

## Full results — 20 trading-day horizon

| Signal | Occurrences | Win rate | Median | Trimmed mean | P25 | P75 |
|---|---:|---:|---:|---:|---:|---:|
| RSI oversold recovery | 43,429 | 54.1% | +0.79% | +1.19% | — | — |
| RSI overbought reversal | 59,655 | 52.3% | +0.29% | +0.01% | — | — |
| MACD golden cross | 144,800 | 50.6% | +0.09% | +0.15% | −2.67% | +2.60% |
| MACD death cross | 144,908 | 53.6% | +0.45% | +0.77% | −2.52% | +2.69% |
| MA20/60 golden cross | 31,391 | 48.8% | −0.04% | −0.07% | −3.09% | +2.24% |
| MA20/60 death cross | 32,003 | 51.7% | +0.24% | +0.58% | −2.70% | +2.86% |
| Combined bullish setup | 7,763 | 49.0% | −0.05% | −0.39% | −2.82% | +3.32% |
| Combined bearish setup | 8,660 | 54.1% | +0.54% | +0.56% | — | — |

Machine-readable data: [signal-results-2026-11.csv](../data/signal-results-2026-11.csv)

---

## The same signal behaves differently on different stocks

This is the finding we consider most useful and least published.

MACD golden cross, 20-day horizon:

| Stock | Occurrences | Win rate | Median return |
|---|---:|---:|---:|
| AAPL | 26 | **69.2%** | **+2.98%** |
| NVDA | 26 | 65.4% | +2.50% |
| TSLA | 29 | 58.6% | +2.16% |
| MSFT | 25 | **48.0%** | **−0.23%** |

A single quoted number for "the golden cross" hides a range this wide. Across every stock with at least
ten occurrences, the MA20/60 golden cross win rate ranged from **63.6%** down to **9.1%**.

---

## Why we report medians, not averages

Small-cap price history contains extreme outcomes. For one signal in this dataset, the arithmetic mean
forward return was **+17.8%** while the median was **+0.09%**. The mean is not describing the typical
outcome; it is describing a handful of outliers.

Every statistic in this report therefore leads with the **median** and a **1%-trimmed mean**. The raw
mean is included for transparency only.

---

## Limitations — read these before citing

1. **Sample period.** Roughly two years. It does not span a full bull/bear cycle.
2. **Gross returns.** No commission, spread or slippage. At a 0.1% round trip most medians fall to zero
   or below.
3. **Time-based exits only.** No stop-loss or take-profit rules.
4. **Liquidity.** Illiquid small caps are over-represented and could not realistically be filled at the
   closing print.
5. **Parameters are conventional, not optimised.** RSI(14), MACD(12,26,9), MA(20/60). Tuning them would
   produce better-looking numbers that would not survive out of sample.
6. **No survivorship correction** for delisted names.
7. **Absolute, not excess, returns.** A positive median may simply reflect the market rising during the
   sample. We have not subtracted a market benchmark, so none of these numbers demonstrate predictive
   value.

**What this is not:** a trading strategy, a forecast, or investment advice. It is a description of what
happened in one particular two-year window.

---

## Method summary

| Item | Detail |
|---|---|
| Universe | 6,867 U.S. equities with ≥250 daily bars |
| Data | Split-adjusted daily OHLCV, end-of-day |
| Entry | Signal-day close |
| Exit | Close 5, 10 or 20 trading days later |
| Statistics | Occurrence count, win rate, median, 1%-trimmed mean, quartiles, best/worst |
| Validation | RSI/MACD cross-checked against TA-Lib, max deviation < 0.0002 |

Full methodology: <https://pulsarsignals.com/methodology.php>
Indicator definitions: [docs/indicator-reference.md](../docs/indicator-reference.md)
Backtest description: [docs/backtesting.md](../docs/backtesting.md)

---

## Citing this report

```
PulsarSignals. "The 2026 Technical Signal Report: What 3.88 million daily bars say
about RSI, MACD and moving-average crosses." November 2026.
https://pulsarsignals.com/backtest.php
```

Data is released under CC0. Please cite the sample period and the limitations above when quoting
figures — a win rate without its occurrence count and its horizon is not a meaningful number.

---

## Contact

Questions about the method, or a request for a different cut of the data (sector, market cap, date
range): the contact form at <https://pulsarsignals.com/contact.php> reaches us directly.

---

*Not investment advice. Past results do not imply future returns.*
