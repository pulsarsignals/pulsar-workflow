# Signal backtest — 2026-11

> Automatically generated from the PulsarSignals price database. Every number below is reproducible from the [indicator definitions](../docs/indicator-reference.md).

## Run metadata

| Item | Value |
|---|---|
| Generated | `2026-11-04T17:15:27Z` |
| Sample start | 2024-01-01 |
| Symbols | 6,867 |
| Daily bars | 3,876,380 |
| Horizons | 5d, 10d, 20d |

## Results

### 5 trading-day horizon

| Signal | Occurrences | Win rate | Median | Trimmed mean | P25 | P75 |
|---|---:|---:|---:|---:|---:|---:|
| RSI oversold recovery | 46,097 | 49.2% | +0.00% | -0.01% | -3.35% | +3.17% |
| RSI overbought reversal | 60,744 | 50.5% | +0.05% | -0.12% | -2.69% | +2.38% |
| MACD golden cross | 148,937 | 50.2% | +0.02% | +0.03% | -2.67% | +2.60% |
| MACD death cross | 148,098 | 52.0% | +0.13% | +0.14% | -2.52% | +2.69% |
| MA20/MA60 golden cross | 31,993 | 46.8% | -0.12% | -0.35% | -3.09% | +2.24% |
| MA20/MA60 death cross | 33,350 | 49.9% | +0.00% | +0.10% | -2.70% | +2.86% |
| Combined bullish setup | 7,982 | 52.3% | +0.18% | +0.28% | -2.82% | +3.32% |
| Combined bearish setup | 8,814 | 54.3% | +0.28% | +0.39% | -2.02% | +2.56% |

### 10 trading-day horizon

| Signal | Occurrences | Win rate | Median | Trimmed mean | P25 | P75 |
|---|---:|---:|---:|---:|---:|---:|
| RSI oversold recovery | 45,142 | 54.2% | +0.54% | +0.86% | -3.88% | +5.14% |
| RSI overbought reversal | 60,287 | 52.4% | +0.20% | +0.03% | -3.82% | +3.53% |
| MACD golden cross | 147,567 | 50.3% | +0.04% | +0.07% | -3.88% | +3.75% |
| MACD death cross | 147,208 | 53.0% | +0.27% | +0.31% | -3.72% | +3.92% |
| MA20/MA60 golden cross | 31,763 | 47.5% | -0.12% | -0.32% | -4.39% | +3.43% |
| MA20/MA60 death cross | 32,954 | 51.1% | +0.14% | +0.34% | -3.82% | +4.31% |
| Combined bullish setup | 7,914 | 52.7% | +0.28% | +0.25% | -4.32% | +4.54% |
| Combined bearish setup | 8,783 | 54.2% | +0.40% | +0.53% | -3.16% | +3.74% |

### 20 trading-day horizon

| Signal | Occurrences | Win rate | Median | Trimmed mean | P25 | P75 |
|---|---:|---:|---:|---:|---:|---:|
| RSI oversold recovery | 43,429 | 54.1% | +0.79% | +1.19% | -6.46% | +7.33% |
| RSI overbought reversal | 59,655 | 52.3% | +0.29% | +0.01% | -5.70% | +5.01% |
| MACD golden cross | 144,800 | 50.6% | +0.09% | +0.15% | -6.03% | +5.34% |
| MACD death cross | 144,908 | 53.6% | +0.45% | +0.77% | -5.23% | +5.65% |
| MA20/MA60 golden cross | 31,391 | 48.8% | -0.04% | -0.07% | -6.47% | +5.09% |
| MA20/MA60 death cross | 32,003 | 51.7% | +0.24% | +0.58% | -5.81% | +6.17% |
| Combined bullish setup | 7,763 | 49.0% | -0.05% | -0.39% | -7.01% | +5.76% |
| Combined bearish setup | 8,660 | 54.1% | +0.54% | +0.56% | -4.70% | +5.07% |

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
