# PulsarSignals — Public Feature Documentation

PulsarSignals.com is a US equities research site built around **end-of-day technical readings and
verifiable, side-by-side comparison**. This repository is the public, plain-English documentation of
what the site does, how its features work, and how its figures are produced.

It is not the site's source code. It contains no operational details, no credentials, and no
per-stock datasets.

---

## Feature index

| Document | Feature covered |
|---|---|
| [Company pages](docs/company-pages.md) | Technical readings, signals, price levels, fundamentals, holders, corporate actions |
| [Comparison pages](docs/comparison-pages.md) | Side-by-side multi-symbol comparison and signal comparison |
| [Signal backtesting](docs/backtesting.md) | How signal performance is measured and how to read the results |
| [Indicator reference](docs/indicator-reference.md) | Exact formulas and periods for every published indicator |
| [Data coverage](docs/data-coverage.md) | Universe, sources, update schedule, freshness policy |

---

## At a glance

- **Company pages** give a complete technical read for a single ticker: RSI, MACD, moving averages,
  Bollinger Bands, ATR, volume and trend indicators, an aggregated signal with a stated confidence,
  ATR-derived support and resistance levels, financial statements, institutional holders and corporate
  actions.
- **Comparison pages** put up to eight symbols in one table, and show how the same signals have
  historically behaved on each of them.
- **A backtest** measures how eight conventional signals performed across the covered universe. The
  full results, including unfavourable ones, are published on the site.
- **A methodology page** documents the formulas and periods behind every figure.

---

## Data policy

All prices are **end-of-day** and refreshed after each US market close. The site does not provide
real-time quotes. Figures are descriptive statistics about historical price behaviour, not forecasts
and not investment advice.

---

## Licence

MIT — see [LICENSE](LICENSE). Documentation text only; no data or application code is included here.
