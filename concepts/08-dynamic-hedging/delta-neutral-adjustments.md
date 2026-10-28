# Delta-neutral adjustments: how the hedge is rebalanced

**One-line definition:** an **adjustment** is a trade in the underlying made only to bring the position's total delta back to zero; because the underlying has no theoretical value, an adjustment does not change the theoretical edge.

## Intuition
Think of the call as a dimmer switch on how much it behaves like the stock. At the start the call behaves like half a stock (delta 50), so we hold the opposite half. When the price rises, the call behaves more like a full stock (delta 54), so our short is now too small, and we **sell more** stock. When the price falls, the call behaves less like stock (delta 35), our short is now too big, and we **buy some back**.

Notice what that does: we sell after prices have gone up and buy after they have gone down. The book puts it bluntly: "we were forced to do what every trader wants to do: buy low and sell high."

## The maths
**Total delta position** (use $+$ for contracts bought and $-$ for contracts sold or short; delta in whole numbers, the underlying is 100):

$$\text{total delta} = \sum (\text{quantity} \times \Delta)$$

For 100 calls and $s$ underlying contracts short:

$$\text{total delta} = 100 \times \Delta_{\text{call}} - 100 \times s$$

**The adjustment.** To return to zero:

$$\text{contracts to trade} = \frac{\text{total delta}}{100}, \qquad \text{positive} \Rightarrow \text{sell}, \quad \text{negative} \Rightarrow \text{buy}$$

Why divide by 100? One underlying contract is 100 deltas, so a total of $+400$ deltas needs $400/100 = 4$ contracts to cancel it.

**Cash flow of the adjustment:** $\text{contracts} \times \text{price}$, positive when selling (cash comes in), negative when buying. [[00-maths-refresher/signs-and-running-totals]]

## Worked example (Figure 8-1)
Start: 100 calls, short 50, delta 50.

| Week | Price | Call delta | Total delta before | Trade | Short in total after |
|---|---|---|---|---|---|
| 1 | 99.50 | 54 | $5{,}400 - 5{,}000 = +400$ | sell 4 | 54 |
| 2 | 92.75 | 35 | $3{,}500 - 5{,}400 = -1{,}900$ | buy 19 | 35 |
| 3 | 95.85 | 43 | $4{,}300 - 3{,}500 = +800$ | sell 8 | 43 |
| 4 | 96.20 | 43 | $4{,}300 - 4{,}300 = 0$ | none | 43 |

Week 2 in words: the stock dropped 6.75, delta fell from 54 to 35, so our short of 54 is 19 too many. Buy 19 at 92.75 (cash out $-1{,}762.25$). The book splits the short into the **original hedge** (50 short) and the **adjustments** (everything else), so after week 2 the adjustments are "long 15" ($-4 + 19 = +15$ bought net). That is why the book's column reads *Short 4*, *Long 15*, *Long 7*...

Across the whole path in Figure 8-1 we sold 86 contracts at an average price of 101.04 and bought 64 at an average of 92.77 (before the final buy-back of 22 at 103.85). That is the "sell high, buy low" pattern in numbers, for this path.

![Weekly prices and the adjustment each week](../../images/ch08-hedge-path.png)

## Why only the underlying?
We *could* adjust with options, but the book trades the underlying "to keep our present calculations as simple as possible and to remain consistent with the theoretical pricing model". An underlying contract always has a delta of 100 and, from an option trader's point of view, **no theoretical value**, so buying or selling it cannot create or destroy theoretical edge.

## Common confusions
- **Adjustments are not mistakes being fixed.** Each one is a planned trade that locks in a small gain from the option's curvature ([[concepts/08-dynamic-hedging/gamma-and-the-unhedged-amount]]).
- **Continuous in theory, discrete in practice.** The model assumes the hedge is adjusted at every moment; we can only trade at intervals, so we make adjustments "as closely as possible" to that ideal. [[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]]
- **The sign of the total delta.** With long calls, a positive total (price rose) means *sell*; with *short puts* the logic is the same because a short put also has positive delta. [[concepts/08-dynamic-hedging/futures-option-hedge-and-variation]]
- **You cannot trade fractional contracts.** The book rounds to whole contracts: 100 calls and 50 underlying, not "0.504 of a contract per call".

## Related
- Chapter: [[chapters/08-dynamic-hedging]]
- Previous: [[concepts/08-dynamic-hedging/series-of-bets-and-dynamic-hedging]]
- Next: [[concepts/08-dynamic-hedging/stock-option-hedge-walkthrough]]
- Earlier: [[concepts/07-risk-measurement-i/delta]], [[concepts/07-risk-measurement-i/risk-measures-of-the-underlying-and-signs]]
- Maths needed: [[00-maths-refresher/signs-and-running-totals]]
- See also: [[glossary]], [[formulas]]
