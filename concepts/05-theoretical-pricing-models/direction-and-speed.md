# Direction and speed

**One-line definition:** a stock buyer only has to be right about *direction*; an option buyer also has to be right about *speed*, because the option expires and its time value decays.

## Intuition
Imagine you think a stock will climb from 100 to 115 in the next five months.

- **Buying the stock:** wait. If it gets to 115 you sell and bank 15. The only question is *whether* it gets there.
- **Buying an option:** the option has a deadline. If the stock reaches 115 *after* the option has expired, you were right about direction and still lose everything you paid.

So an option is a bet on direction **and** on timing. If the market is slow, a correct directional guess can still lose money.

## Worked example (the book's)
Stock at 100. You expect 115 within five months.

| Choice | Cost | If stock reaches 115 *before* expiry | If stock reaches 115 only *after* expiry |
|---|---|---|---|
| 110 call, 3 months | 2 | intrinsic value $115 - 110 = 5$, profit $5 - 2 = 3$ | option expired worthless, lose 2 |
| 110 call, 6 months | 6 | worth *at least* 5 (its intrinsic value), but it cost 6, so possibly a loss | (not applicable: the option lives for six months, longer than the five-month forecast) |

Step by step for the 6-month call:
1. Buy at 6.
2. When the stock hits 115 the call is worth at least $115 - 110 = 5$.
3. Worth *at least* 5 does not mean worth 6 or more, so you might still show a loss. The longer option is safer against being too slow, but you paid extra for that safety.

The longer, more expensive option removes the deadline problem but adds a cost problem. There is no free answer, which is why the price of the option matters (and why a pricing model is needed).

## Why this matters
- The book says many option strategies depend **only on the speed of the market, not on its direction** (it develops these later, in the spreading chapters).
- If you are very good at predicting direction, you may be better off trading the underlying itself.
- Speed is measured by **volatility** (Chapter 6): how fast, and how far, prices move.

## Common confusions
- "Speed" does not mean the stock must rise quickly. It means *how much the price moves around* in the time available. A very jumpy stock can reach a faraway price; a quiet one cannot.
- Being right about direction is necessary for a long call or put, but not sufficient.

## Related
- Chapter: [[chapters/05-theoretical-pricing-models]]
- Earlier: [[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]] (time value is what is lost if the market is slow)
- Next: [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]
- See also: [[glossary]], [[formulas]]
