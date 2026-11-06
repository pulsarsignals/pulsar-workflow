# Company Pages

**URL pattern:** `/stock_analysis/{ticker}` — for example `/stock_analysis/AAPL`

A company page is the primary unit of the site. It combines a current technical read, the underlying
fundamentals, ownership data and historical signal behaviour on one page.

---

## 1. At-a-glance technical summary

The top of the page states the current technical stance in one sentence:

> *AAPL is showing a **Bearish** technical setup (SELL, 75% confidence) — RSI 41.7, MACD below its
> signal line. Key support $324.05, resistance $339.75.*

The three components are:

| Component | Meaning |
|---|---|
| **Direction** | Bullish / Bearish / Neutral, derived from the aggregated signal |
| **Confidence** | How much the underlying indicators agree with each other; disagreement lowers it |
| **Price levels** | Nearest support and resistance, from the ATR formula (see [Indicator reference](indicator-reference.md)) |

A consistency check runs before price levels are displayed. If the computed support is not below the
current close, or resistance not above it, the underlying price history is considered stale and the
levels are **withheld** rather than shown as contradictory numbers.

---

## 2. Indicators

The page shows current values and recent series for:

- **RSI (14)** — momentum position, conventionally overbought above 70 and oversold below 30
- **MACD (12, 26, 9)** — MACD line, signal line and histogram
- **Moving averages** — short, medium and long simple moving averages
- **Bollinger Bands (20, 2σ)** — upper, middle and lower bands
- **ATR (14)** — average true range, used as the volatility unit for price levels
- **ADX / +DI / −DI**, **CCI**, **Stochastic**, **Parabolic SAR**, **OBV** — supporting trend and
  volume readings

Each indicator contributes a direction and a strength. These are aggregated into one **overall
signal** (BUY / SELL / NEUTRAL) with a confidence figure. The signal breakdown is shown alongside the
aggregate so the reasoning is visible rather than hidden behind a single label.

---

## 3. Key price levels

Support and resistance are derived from the latest close and the current ATR:

| Level | Formula |
|---|---|
| Weak support / resistance | `price ∓ 1 × ATR` |
| Medium support / resistance | `price ∓ 2 × ATR` |
| Strong support / resistance | `price ∓ 3 × ATR` |
| Stop-loss suggestions | `price ∓ 0.8 / 1.5 / 2.5 × ATR`, direction depending on the signal |

Because the levels are anchored to the latest close, support is always below the current price and
resistance always above it. See [Indicator reference](indicator-reference.md) for the exact calculation.

---

## 4. Fundamentals

### 4.1 Financial statements

Three financial statement groups are shown for the most recent reported periods, with quarterly and
annual views:

- **Income statement** — revenue, gross profit, operating income, EBITDA, net income, EPS
- **Balance sheet** — assets, liabilities, equity, debt, cash, inventory, receivables
- **Cash flow** — operating, investing and financing cash flows, capital expenditure, free cash flow

Figures come from company filings distributed by the site's market data provider. Where a metric is
not applicable (for example a P/E ratio for a company with negative earnings, or a dividend yield for
a non-payer) the page shows `N/A` rather than a misleading number.

### 4.2 Profitability and revenue trend

Up to eight recent reported quarters are reduced to four comparable figures per quarter:

| Column | Definition |
|---|---|
| Revenue | Reported total revenue for the period |
| Gross margin | Gross profit ÷ revenue |
| Operating margin | Operating income ÷ revenue |
| Net margin | Net income ÷ revenue |

A trailing-twelve-month snapshot above the table shows gross margin, EBITDA margin, net margin and
year-over-year revenue growth.

Rules:

- Ratios are computed from reported income statements sourced from **SEC EDGAR XBRL**, not copied
  from a third-party summary.
- Where a period has both quarterly and annual rows for the same date, the quarterly row is preferred.
- A quarter with zero or missing revenue is skipped rather than producing a meaningless percentage.
- Fewer than two reported periods means no trend table at all.
- The table shows the three most recent quarters by default; the remaining rows stay in the page and
  are revealed by a client-side "Show all quarters" control.

### 4.3 Dividend summary

For dividend payers the Stock Actions card leads with dividend yield, payout ratio, the sum of the last
four dividends and the most recent dividend (date and amount). Non-payers have no dividend block — no
zero and no placeholder.

---

## 5. Institutional holders

A "Holder List Top 20" table lists the largest reported institutional positions: holder name, holder
type, shares held, percentage held and the report date. It reflects the most recent disclosure
available from the provider; institutional holdings are reported with a delay of several weeks to a
few months after the reporting date shown in the table.

---

## 6. Corporate actions

A "Stock Actions" section lists dividends and stock splits with their dates and values.

---

## 7. Per-symbol signal history

A table titled *"How these signals performed on {ticker}"* shows, for each signal and for 5 / 10 / 20
trading-day horizons:

- number of historical occurrences since January 2024
- win rate
- median forward return
- best and worst outcomes

Small samples are shown as-is and explicitly labelled as not statistically meaningful. The same data
is used on comparison pages to compare symbols side by side. The market-wide version is documented in
[Signal backtesting](backtesting.md).

---

## 8. Structured data

Company pages emit `WebPage` / `Article` JSON-LD together with `QuantitativeValue` blocks for the
published indicator readings. When price levels are withheld due to stale data, the corresponding
structured-data values are left empty rather than populated with incorrect numbers.

A separate `Dataset` block describes the quarterly profitability table (revenue, gross/operating/net
margin, temporal coverage), with `PropertyValue` entries for the trailing-twelve-month figures. It is
emitted only when at least two reported periods exist.

---

## Notes

- All prices are end-of-day and updated after each US market close.
- A page returns 404 when the requested ticker is not present in the covered universe.
- Nothing on the page is investment advice.
