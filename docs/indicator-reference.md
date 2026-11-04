# Indicator Reference

Every published indicator uses a fixed, conventional parameter set. No parameter is optimised against
historical results.

---

## RSI — Relative Strength Index

- **Period:** 14, on daily closes
- **Method:** Wilder's smoothing of average gains and losses, scaled to 0–100
- **Conventional zones:** above 70 overbought, below 30 oversold
- **Signals derived:** `RSI_OVERSOLD` (crosses back above 30 from below), `RSI_OVERBOUGHT` (crosses
  back below 70 from above)

RSI is a momentum measure, not a reversal signal. A strong trend can keep RSI above 70 or below 30 for
many sessions.

---

## MACD — Moving Average Convergence Divergence

- **Fast EMA:** 12
- **Slow EMA:** 26
- **Signal EMA:** 9
- **Outputs:** MACD line = EMA(12) − EMA(26); signal line = EMA(9) of the MACD line; histogram = the
  difference between the two
- **Signals derived:** `MACD_GOLDEN` (MACD line crosses above signal line), `MACD_DEATH` (crosses below)

A shrinking histogram on a negative reading means downward momentum is fading, even though the reading
is still negative.

---

## Moving Averages

- **Short / medium / long:** SMA(20), SMA(60) and a longer window for the company page's MA panel
- **Comparison pair:** SMA(20) and SMA(60)
- **Signals derived:** `MA_GOLDEN` (SMA20 crosses above SMA60), `MA_DEATH` (crosses below)

A moving-average cross is slower and less frequent than a MACD cross, and is less prone to whipsaw in
sideways markets.

---

## Bollinger Bands

- **Period:** 20
- **Width:** 2 standard deviations above and below the SMA(20) middle band
- **Outputs:** upper, middle and lower band series

Price near the upper band indicates an extended move, not automatically a sell; the same applies in
reverse to the lower band.

---

## ATR — Average True Range

- **Period:** 14
- **True range:** the greatest of high − low, |high − previous close|, |low − previous close|
- **Use:** the volatility unit for key price levels

### Key price levels

For the latest close `P` and current ATR `A`:

| Level | Support | Resistance |
|---|---|---|
| Weak | `P − 1 × A` | `P + 1 × A` |
| Medium | `P − 2 × A` | `P + 2 × A` |
| Strong | `P − 3 × A` | `P + 3 × A` |

Stop-loss suggestions use tighter multiples (0.8 / 1.5 / 2.5 × ATR), with the direction depending on
the overall signal. Because all levels are anchored to the latest close, support is always below the
current price and resistance always above it. If that relationship does not hold, the underlying price
history is stale and the levels are withheld.

---

## Supporting Indicators

| Indicator | Parameters | Purpose |
|---|---|---|
| **ADX / +DI / −DI** | 14 | Trend strength and direction |
| **CCI** | 20 | Momentum oscillator |
| **Stochastic** | 14, with smoothing | Position within the recent range |
| **Parabolic SAR** | 0.02 acceleration, 0.2 maximum | Trend-following stop and reverse |
| **OBV** | Cumulative volume by price direction | Accumulation / distribution |

---

## Combined Setups

- `COMBO_BULL`: MACD golden cross **and** RSI below 50 **and** price above SMA(20)
- `COMBO_BEAR`: MACD death cross **and** RSI above 50 **and** price below SMA(20)

These were included to test whether combining filters improves on a single signal. In the published
sample they did not.

---

## Overall Signal and Confidence

Each indicator contributes a direction (buy, sell or neutral) and a strength. The contributions are
aggregated into:

- an **overall signal**: BUY / SELL / NEUTRAL
- a **confidence** figure reflecting how much the indicators agree

Agreement raises confidence; disagreement lowers it. A mixed set of readings should produce a weaker
signal, not a falsely tidy one.

---

## Validation

The numpy implementations were cross-checked against TA-Lib on 11,566 daily bars:

| Indicator | Maximum deviation |
|---|---|
| RSI(14) | < 0.000001 |
| MACD line | < 0.000012 |
| MACD signal | < 0.000156 |

---

## Notes

All calculations use end-of-day split-adjusted closes. Indicators describe past price behaviour; none
of them reliably predicts the next move.
