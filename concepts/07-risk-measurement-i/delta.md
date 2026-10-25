# Delta

**One-line definition:** the delta ($\Delta$) is how much an option's theoretical value changes when the underlying price changes by 1 point, and so measures the option's *directional* risk.

## Intuition
Picture the call's value as a curve against the underlying price ([[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]]). Far out of the money the curve is nearly flat: moving the stock hardly changes the option. Deep in the money the curve rises one-for-one with the stock, like owning the stock. In between it is a slope somewhere from 0 to 1. **The delta is that slope.**

![Delta and gamma curves](../../images/ch07-delta-and-gamma.png)

## The maths
Delta is the rate of change of the option value $V$ with respect to the underlying price $S$ ([[00-maths-refresher/derivatives-and-rates-of-change]]):

$$\Delta = \frac{\text{change in option value}}{\text{change in underlying price}}$$

- A call has $0 \le \Delta \le 1$ (0 far out of the money, 1 deep in the money). A call can never gain or lose value faster than the stock, nor move against it.
- A put has $-1 \le \Delta \le 0$. The negative sign means it moves *opposite* to the underlying.
- The **underlying contract** itself always has $\Delta = 1$.

**Whole-number convention.** Traders drop the decimal point: a delta of 0.56 is "56", the underlying is "100", calls run 0 to 100 and puts $-100$ to 0. (This came from US stock options, where one delta equalled one share and a contract was 100 shares.) When using a delta in arithmetic on prices, convert back to a decimal.

Estimating a small change: if $\Delta = 0.25$ and the stock rises 1.00, the option rises about 0.25. If $\Delta = 0.75$ and the stock rises 0.60, the option rises about $0.75 \times 0.60 = 0.45$.

## Four ways to read the same number
The book gives four interpretations. They are the same mathematics, used differently.

**1. Rate of change (the definition).** A delta of 40 means the option moves 40% as fast as the underlying.

**2. Hedge ratio.** To make a position neutral to small price moves ([[concepts/05-theoretical-pricing-models/riskless-hedge-and-hedge-ratio]]) you need underlying contracts equal to $100/\Delta$ per option:

| Option | Hedge ratio $100/\Delta$ | Meaning |
|---|---|---|
| Call, $\Delta = 50$ | $100/50 = 2/1$ | sell (buy) 1 underlying per 2 options bought (sold) |
| Call, $\Delta = 40$ | $100/40 = 5/2$ | sell (buy) 2 underlying per 5 options bought (sold) |
| Put, $\Delta = -75$ | $100/(-75) = 4/(-3)$ | **buy** (sell) 3 underlying per 4 puts bought (sold) |

A position is **delta neutral** when its deltas add to 0. Use $+$ for contracts bought and $-$ for contracts sold:

| Position | Delta arithmetic | Total |
|---|---|---|
| Buy 2 calls (delta 50), sell 1 underlying | $+2 \times 50 - 1 \times 100 = +100 - 100$ | 0 |
| Sell 4 puts (delta $-75$), sell 3 underlying | $-4 \times (-75) - 3 \times 100 = +300 - 300$ | 0 |

(In the project PDF the book appears to print the second line as "$+4 \times -75$", which would not add to zero; the sign of the 4 should be negative because the puts are *sold*.) Selling puts gives positive delta, and selling stock cancels it.

**3. Equivalent underlying position.** Each 100 deltas is theoretically one underlying contract. Owning 10 options with delta 50 is $10 \times 50 = +500$ deltas, about long 5 contracts (500 shares for stock options). Selling 20 puts of delta $-25$ is $-20 \times -25 = +500$ as well. Position value changes at about 5 times the stock's rate: if the stock rises 2.00, the position gains about 10.00; if it falls 1.25, it loses about 6.25.

**4. Probability.** Ignoring sign, delta is roughly the chance the option finishes in the money. A 25-delta option has about a 25% chance, a 75-delta about 75%. At the money the delta is near 50 because, if price changes are random, it is about equally likely to finish either side.

## Worked example (Figure 7-13: stock 99.50, 91 days, volatility 25%)
June 100 call: theoretical value 5.44, delta 56, gamma 3.2.
- The call moves about $0.56 \times 1.00 = 0.56$ for a 1-point rise. The model gives: 99.50 $\to$ 100.50 changes the value from 5.435 to 6.008 (+0.572), and from 98.50 to 100.50 averages 0.556 per point. The delta of 0.56 is the slope at 99.50.
- To hedge 10 calls: $10 \times 56 = 560$ deltas, so sell 5.6 stock contracts (560 shares).
- June 100 put: delta $-44$. $\Delta_{\text{call}} - \Delta_{\text{put}} = 56 - (-44) = 100$, which holds for a call and put with the same strike and expiry.

## Common confusions
- **Delta is not the probability, only close.** Interest and dividends distort it, and what matters for profit is also *how much* an option finishes in the money. A seller of a 10-delta option may win 9 times in 10, then lose more on the tenth than all nine premiums. Win frequency alone is not an edge.
- **It is an instantaneous measure.** Valid only for small moves, because delta itself changes ([[concepts/07-risk-measurement-i/gamma]]).
- **An option is not a surrogate for stock.** Delta equals an underlying position only for the directional risk; the option is also sensitive to volatility and time. Someone who looks only at delta may ignore larger risks.
- **At the forward, not at the stock price.** Option values are based on the forward price, so the option closest to a delta of 50 is the one at the *forward*. Book footnote: stock 100, one year, 10% rate, forward 110. The 110 call is close to 50, and the 105 call, seemingly out of the money, has a delta above 50. Our model check (volatility 20%): 110 call 55, 105 call 64, 100 call 73.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/what-moves-option-values]]
- Next: [[concepts/07-risk-measurement-i/gamma]]
- Later: Chapter 8 (dynamic hedging), Chapter 9 (more on delta)
- See also: [[glossary]], [[formulas]]
