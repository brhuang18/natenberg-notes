# Adjusting a volatility spread (keeping it delta neutral)

**One-line definition:** a spread that starts delta neutral will not stay that way (the underlying moves, volatility changes, time passes), so before trading you should decide *how* you will adjust it: at regular intervals, when delta reaches a limit, by feel, or not at all.

## Intuition
A traditional pricing model assumes you **adjust continuously**. In real markets that is neither possible nor sensible (costs, and no one can be certain the model's deltas are right). So the practical question is: what rule will you use? The book gives four.

## The four approaches (pages 201-203)
1. **Adjust at regular intervals.** Volatility is measured over regular periods (daily, weekly), so adjust at the same rhythm: daily if your estimate comes from daily changes, weekly if weekly. This tries to mimic the model's assumption as closely as you can ([[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]]).

2. **Adjust when you reach a number of deltas.** Pick how many deltas long or short you are comfortable carrying, and adjust when you hit it. You cannot know in advance how often that will be: sometimes often, sometimes for a long time not at all. The right limit depends on your capital, the size of your positions and your experience. A new independent trader may be uncomfortable with 200 deltas; a large firm may treat several thousand deltas as approximately neutral.

3. **Adjust by feel.** If you have good market sense, use it. Example: underlying at 50.00, delta neutral, gamma $-200$. If the market falls 2 points, the delta changes by

$$\Delta\text{delta} = \text{gamma} \times \text{move} = (-200) \times (-2.00) = +400$$

so you are about 400 deltas long. If 400 is your limit you would adjust. But if you also know 48.00 is strong support, you might skip the adjustment, expecting a rebound. If right, you avoided an unprofitable adjustment; if wrong, you regret it. If you are right more often than not, there is no reason not to use that skill.

4. **Do not adjust at all.** This is approach 2 with the limit equal to the **maximum delta the position can take on**. For example, five short straddles can reach at most $\pm 500$ deltas (each straddle is at most $\pm 100$). It saves all later transaction costs, but if the delta becomes large, **direction starts to matter more than volatility**. If the trade was based on a view on volatility, switching to a view on direction is usually wrong. If you do not want to adjust *and* do not want direction to dominate, the only choice left is to **close the position**. So decide up front under what conditions you will hold and under what conditions you will close.

## Why gamma tells you how fast the delta drifts
Gamma is "delta per point" ([[concepts/07-risk-measurement-i/gamma]]). A position with $-200$ gamma loses 200 deltas of "longness" per point of rise and gains 200 per point of fall; the bigger the gamma, the sooner you hit your delta limit. That is why short straddles and strangles (large negative gamma) need the most attention, and butterflies (small gamma) the least.

## Common confusions
- **"Delta neutral" is not "adjusted every day".** It is a decision you must make explicitly.
- **Adjusting costs money** (bid-ask and fees) and, for a long-gamma position, tends to lock in small profits; for a short-gamma position, to lock in small losses ([[concepts/08-dynamic-hedging/gamma-and-the-unhedged-amount]]).
- **Not adjusting is not a free choice.** It converts the spread into a more directional position.

## Related
- Chapter: [[chapters/11-volatility-spreads]]
- Previous: [[concepts/11-volatility-spreads/choosing-a-spread-by-implied-volatility]]
- Next: [[concepts/11-volatility-spreads/submitting-a-spread-order]]
- Earlier: [[concepts/08-dynamic-hedging/delta-neutral-adjustments]], [[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]], [[concepts/07-risk-measurement-i/gamma]]
- Maths needed: [[00-maths-refresher/derivatives-and-rates-of-change]]
- See also: [[glossary]], [[formulas]]
