# Data Coverage

A short description of the data behind the site's features.

---

## 1. Market data

| Item | Description |
|---|---|
| Asset class | US-listed equities, ETFs and funds |
| Price series | Daily open, high, low, close, volume |
| Adjustment | Prices are split-adjusted |
| Timing | **End-of-day**; refreshed after each US market close |
| Storage | Held locally so charts, comparisons and signals all draw on the same figures |

The site does **not** provide real-time or intraday quotes. Any last-price figure shown is the most
recent end-of-day close.

---

## 2. Fundamentals

Three statement groups are stored and refreshed on a weekly basis:

- **Income statement** — revenue, margins, operating income, net income, EPS
- **Balance sheet** — assets, liabilities, equity, debt, cash and equivalents
- **Cash flow** — operating, investing and financing flows, capital expenditure, free cash flow

Quarterly and annual periods are both kept. Figures originate from company filings distributed by the
site's market-data provider.

---

## 3. Corporate actions and ownership

| Dataset | Contents | Refresh |
|---|---|---|
| Dividends and splits | Action date, type, value | Weekly |
| Institutional holders | Holder name, type, shares, percentage, report date | Weekly |

Institutional holdings are disclosed with a delay of several weeks to a few months after the reporting
date shown in the table.

---

## 4. Derived data

| Dataset | Description |
|---|---|
| Computed indicators | RSI, MACD, moving averages, Bollinger Bands, ATR, ADX, CCI, Stochastic, SAR, OBV — recomputed daily from stored prices |
| Overall signal | Aggregated direction with a confidence figure |
| Key price levels | Support, resistance and stop-loss suggestions from ATR |
| Per-symbol signal statistics | Historical occurrences, win rates and forward returns per signal and horizon |

Indicator calculations and signal definitions are documented in the
[Indicator reference](indicator-reference.md).

---

## 5. Universe for published statistics

The market-wide backtest uses symbols with at least 250 daily bars in the sample period — roughly
6,800 equities and 3.88 million daily bars from January 2024 onward. Company and comparison pages
cover a wider universe; pages are only generated for symbols with sufficient price history.

---

## 6. Freshness behaviour

The site prefers an honest gap over a stale number:

- If a symbol's latest bar is older than the site's freshness threshold, its technical indicators are
  not recomputed from older data.
- If computed support/resistance levels are inconsistent with the current close, the levels are
  withheld rather than displayed.
- Where a metric is not meaningful (negative earnings, no dividend), the page shows `N/A`.

---

## 7. Scope

No per-stock dataset, database schema or connection detail is included in this documentation
repository. Data is descriptive of historical behaviour and is not investment advice.
