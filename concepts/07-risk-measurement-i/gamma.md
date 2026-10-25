# Gamma

**One-line definition:** the gamma ($\Gamma$) is the rate of change of the delta as the underlying price changes; it measures how quickly your directional exposure changes, a measure of *magnitude* or *speed* risk.

## Intuition
If delta is "how steep is the road", gamma is "how fast is the road bending". The delta graph is not a straight line: it flattens toward 0 (or 100) at the extremes and is steepest near the exercise price. The slope of that delta graph is the gamma. So gamma is biggest for options near the money.

## The maths
Gamma is expressed as **deltas gained or lost per one-point move**:

$$\Delta_{\text{new}} = \Delta_{\text{old}} + \text{(price change)} \times \Gamma$$

- If the underlying **rises**, add the gamma to the old delta.
- If the underlying **falls**, subtract the gamma.

Example: gamma 5, delta 25. A 1-point rise gives delta 30; another point, 35. A 1-point fall gives 20; another, 15. (This assumes the gamma stays constant, which it does not; it changes too.)

**Same for calls and puts.** A call and a put with the same strike and expiry have the *same* gamma, and it is always positive. The delta graphs for calls and puts have the same shape, always sloping upward. Check with at-the-money options and gamma 5:

| | Delta now | Stock +1 (add 5) | Stock $-1$ (subtract 5) |
|---|---|---|---|
| Call | 50 | 55 (moving into the money) | 45 (moving out) |
| Put | $-50$ | $-45$ (moving out of the money) | $-55$ (moving into the money) |

Both deltas *increase* when the price rises: the put's delta goes from $-50$ to $-45$, which is a bigger (less negative) number.

## Long and short gamma
- Buy options (calls *or* puts): **long gamma**.
- Sell options: **short gamma**.
- For a combined position, add the gammas (positions are additive, [[concepts/07-risk-measurement-i/risk-measures-of-the-underlying-and-signs]]).

**What a positive gamma wants.** Adding a positive number as the stock rises and subtracting as it falls means your delta gets longer in a rising market and shorter in a falling one. You win from big moves.

**What a negative gamma does.** Adding a negative number as the stock rises makes the delta more negative, and subtracting a negative as it falls makes the delta more positive. Either way the position gets worse. Only a quiet market helps.

## Worked example: Position 1 from Figure 7-14
$-10$ June 95 calls and $+7$ underlying contracts: total delta $-10$, total gamma $-28$.

| Stock | Delta |
|---|---|
| 99.50 | $-10$ |
| 100.50 (rise 1) | $-10 + (-28) = -38$ |
| 101.50 (rise 1 more) | $-38 + (-28) = -66$ |
| 98.50 (fall 1) | $-10 - (-28) = +18$ |
| 97.50 (fall 1 more) | $+18 - (-28) = +46$ |

As the market rises the position becomes more negative-delta, and the more it rises the more we want it to fall. As it falls, the delta turns positive, and we want it to rise. We do not want it to rise and we do not want it to fall: **we want it to sit still**.

## Delta is direction, gamma is magnitude
| Gamma position | You want the underlying to... |
|---|---|
| Positive | make big moves, or move very quickly |
| Negative | sit still, or move very slowly |

Together, delta and gamma describe direction and speed. In Position 1, we want a slow (negative gamma), downward (negative delta) move. The worst case is a swift upward move: wrong on both direction *and* speed.

New traders are often warned off large gamma positions, especially negative ones, because the directional risk can change very fast.

## Common confusions
- **Gamma is positive for puts too.** The sign convention that "calls positive, puts negative" belongs to delta only.
- **Gamma versus vega.** Gamma is about *realized* volatility (does the underlying actually move?). Vega is about *implied* volatility (what do option prices imply?). They are often but not always correlated ([[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]]).
- **Gamma is large near the money** and small far from it; the 100 strike has the biggest gamma in Figure 7-13 (3.2) and the 90 and 110 strikes less (2.0, 2.6).
- **Gamma is not constant.** It changes as the price, time and volatility change, as do all risk measures.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/delta]]
- Next: [[concepts/07-risk-measurement-i/estimating-option-value-with-delta-and-gamma]]
- See also: [[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]], [[glossary]], [[formulas]]
