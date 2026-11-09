# Signal backtest — 2026-11

> Automatically generated from the PulsarSignals price database. Every number below is reproducible from the [indicator definitions](../docs/indicator-reference.md).

## Run metadata

| Item | Value |
|---|---|
| Generated | `2026-11-09T07:32:29Z` |
| Sample start | 2024-01-01 |
| Symbols | 7,541 |
| Daily bars | 4,205,677 |
| Horizons | 5d, 10d, 20d |

## Results

### 5 trading-day horizon

| Signal | Occurrences | Win rate | Median | Trimmed mean | P25 | P75 |
|---|---:|---:|---:|---:|---:|---:|
| RSI oversold recovery | 50,064 | 48.8% | +0.00% | -0.11% | -3.35% | +3.07% |
| RSI overbought reversal | 64,530 | 50.2% | +0.03% | -0.11% | -2.66% | +2.35% |
| MACD golden cross | 161,198 | 49.5% | +0.00% | -0.07% | -2.65% | +2.50% |
| MACD death cross | 160,072 | 52.0% | +0.12% | +0.17% | -2.44% | +2.61% |
| MA20/MA60 golden cross | 34,816 | 46.2% | -0.10% | -0.46% | -3.00% | +2.11% |
| MA20/MA60 death cross | 36,411 | 49.5% | +0.00% | +0.09% | -2.60% | +2.72% |
| Combined bullish setup | 8,695 | 51.3% | +0.10% | +0.18% | -2.82% | +3.16% |
| Combined bearish setup | 9,499 | 54.4% | +0.28% | +0.37% | -1.94% | +2.49% |

### 10 trading-day horizon

| Signal | Occurrences | Win rate | Median | Trimmed mean | P25 | P75 |
|---|---:|---:|---:|---:|---:|---:|
| RSI oversold recovery | 49,149 | 53.5% | +0.43% | +0.66% | -3.93% | +4.98% |
| RSI overbought reversal | 64,084 | 52.2% | +0.18% | +0.04% | -3.77% | +3.49% |
| MACD golden cross | 159,611 | 49.7% | +0.00% | -0.04% | -3.83% | +3.60% |
| MACD death cross | 159,030 | 52.8% | +0.24% | +0.32% | -3.62% | +3.79% |
| MA20/MA60 golden cross | 34,531 | 47.0% | -0.11% | -0.47% | -4.30% | +3.22% |
| MA20/MA60 death cross | 35,980 | 50.7% | +0.09% | +0.32% | -3.69% | +4.10% |
| Combined bullish setup | 8,607 | 51.8% | +0.19% | +0.12% | -4.27% | +4.34% |
| Combined bearish setup | 9,460 | 53.9% | +0.34% | +0.49% | -3.03% | +3.60% |

### 20 trading-day horizon

| Signal | Occurrences | Win rate | Median | Trimmed mean | P25 | P75 |
|---|---:|---:|---:|---:|---:|---:|
| RSI oversold recovery | 47,258 | 53.7% | +0.68% | +0.92% | -6.45% | +7.09% |
| RSI overbought reversal | 63,314 | 52.1% | +0.27% | +0.04% | -5.66% | +4.93% |
| MACD golden cross | 156,677 | 50.0% | +0.01% | -0.01% | -5.97% | +5.08% |
| MACD death cross | 156,710 | 53.3% | +0.39% | +0.71% | -5.15% | +5.44% |
| MA20/MA60 golden cross | 34,088 | 48.1% | -0.08% | -0.32% | -6.40% | +4.80% |
| MA20/MA60 death cross | 35,013 | 51.5% | +0.19% | +0.61% | -5.56% | +5.92% |
| Combined bullish setup | 8,444 | 48.6% | -0.06% | -0.47% | -6.94% | +5.54% |
| Combined bearish setup | 9,347 | 53.6% | +0.46% | +0.44% | -4.57% | +4.88% |

## How to read this

- **Win rate** is the share of occurrences with a positive forward return.
- **Median** is the middle observation; it is the primary statistic here because small-cap price history contains extreme outliers that make an arithmetic mean meaningless.
- **Trimmed mean** discards the top and bottom 1% before averaging.
- A high win rate with a small median means many tiny gains and a few large losses.

## Limitations

1. The sample spans roughly two years and does not cover a full market cycle.
2. Returns are **gross** — no commission, spread or slippage. At a 0.1% round trip, most medians here fall to zero or below.
3. Exits are time-based only; no stop-loss or take-profit is applied.
4. Illiquid small caps are over-represented and could not realistically be filled at the closing print.
5. Signal parameters are conventional but arbitrary; other periods give different numbers.
6. No survivorship correction for delisted names.
7. These are **absolute** returns, not excess returns over a market benchmark. A positive median may simply reflect the market rising.

## Data

- Machine-readable: [`data/signal-results-2026-11.csv`](../data/signal-results-2026-11.csv)
- Live version: <https://pulsarsignals.com/backtest.php>

## Disclaimer

Descriptive statistics about historical price behaviour. Not investment advice, not a trading strategy, and not a forecast.
