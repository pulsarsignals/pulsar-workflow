# Comparison Pages

**URL pattern:** `/stock_compare/{A}_vs_{B}` — for example `/stock_compare/AAPL_vs_MSFT`

Comparison pages put two or more symbols side by side. The site supports up to eight symbols in one
view, and covers both two-symbol and three-symbol comparisons.

---

## 1. Comparison summary

The top of the page states the technical stance of each symbol in one line, for example:

> *MSFT is showing a bullish technical setup; AAPL is showing a bearish technical setup.*

This gives an immediate answer to the question behind most "X vs Y" searches — *which one looks
better right now* — before the underlying numbers are presented.

---

## 2. Basic information table

A grid compares, for every symbol in the comparison:

| Metric | Notes |
|---|---|
| Symbol and company name | With a link to the full company page |
| Current price | End-of-day close |
| Daily change | Absolute and percentage |
| Day range | Low – high |
| Market capitalisation | Formatted for readability |
| P/E ratio | `N/A` when not meaningful |
| EPS | Most recent reported |
| Dividend yield | `N/A` for non-payers |
| Sector / industry | Provider classification |
| 52-week change | Percentage |

---

## 3. Technical comparison

Key price levels, stop-loss suggestions and technical indicator readings are shown per symbol in the
same grid, so support, resistance and signal values can be compared directly rather than read one page
at a time.

---

## 4. Signal comparison

A dedicated section, *"How these signals performed on each stock"*, compares each symbol's historical
signal statistics at a 20 trading-day horizon:

| Signal | AAPL | MSFT |
|---|---|---|
| MACD golden cross | 69% (26 occurrences) | 48% (25 occurrences) |
| MA20/60 golden cross | 83% (6 occurrences) | 56% (9 occurrences) |
| RSI oversold recovery | 50% (6 occurrences) | 50% (8 occurrences) |

The number of occurrences is shown next to each win rate, so a rate based on a handful of events is
not mistaken for a track record. Symbols without enough history show a dash.

The underlying statistics are the same per-symbol data described in [Company pages](company-pages.md),
computed from end-of-day prices from January 2024 onward.

---

## 5. Canonical URLs

Symbols inside a comparison URL are kept in a stable sorted order, and the page's canonical tag uses
that same order. This means a comparison requested as `NVDA_vs_AMD` and one requested as
`AMD_vs_NVDA` resolve to the same canonical page, avoiding duplicate content.

---

## 6. Availability

A comparison returns 404 if fewer than two of the requested symbols are present in the covered
universe. Invalid or unknown tickers are rejected rather than rendering an empty comparison.

---

## Notes

- All figures are end-of-day and updated after each US market close.
- Comparisons are descriptive, not recommendations. A symbol showing a better historical win rate is
  not a prediction of future performance.
