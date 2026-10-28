# Implied volatility moves: closing early or holding the hedge

**One-line definition:** you do not always have to hold a dynamic hedge to expiration: if implied volatility rises to your forecast you can close at once and take the whole theoretical profit, and if it falls first you show a temporary loss that does not change the plan.

## Intuition
The hedge earns its profit by waiting for the stock to move enough. There is a shortcut. The reason the call looks cheap at 5.00 is that the market is pricing it at a **32.40%** implied volatility while we think the stock will move at **37.62%**. If the market ever comes round to our view, the call simply becomes worth 5.89 and we can sell it. No waiting for ten weeks of adjustments.

But the market owes us nothing. Option prices are driven by supply and demand, not just by theory, and implied volatility can drift against us even if we are right about the stock.

## Three scenarios (call bought at 5.00, 100 options, hedged with 50 underlying contracts)
Our model reproduces the book's prices:

| Implied volatility becomes | June 100 call price | Profit now (100 options) |
|---|---|---|
| 32.40% (where we bought) | 5.00 | 0 |
| **37.62%** (our forecast) | **5.89** | $100 \times (5.89 - 5.00) = +89$ |
| 30.35% (the book's adverse case) | 4.65 | $100 \times (4.65 - 5.00) = -35$ |

**Good case: implied volatility jumps to 37.62%.** The call rises from 5.00 to 5.89. Sell the 100 calls for $+89$. To finish, buy back the 50 underlying contracts we sold. Implied volatility is a property of options, not of the underlying, so the underlying should still be at 97.70. Buying 50 contracts at the price we sold them gives zero profit or loss on the stock, so the total is exactly the 89.00 the model predicted. "If we can do all this, there is no reason to hold the position for the full 10 weeks."

**How likely is this?** Occasionally implied volatility moves swiftly, but more often it moves gradually, following gradual changes in the underlying's own volatility: as the stock fluctuates faster, demand for options rises, and implied volatility rises. If the stock begins fluctuating faster than 32.40%, we can expect implied volatility to rise toward our target. But no guarantee: "option prices are subject to a wide variety of market forces, not all of them theoretical." If it never revalues, we hold and adjust for the full 10 weeks.

**Bad case: implied volatility falls to 30.35%.** The call drops to 4.65 and we are down $-35.00$ right away. Does that mean the trade was bad? No: if the volatility forecast is still right, the options will still be worth 5.89 by expiration, and by holding and adjusting we expect the full 89.00. The temporary loss is "something with which all traders must learn to cope".

## The maths
Nothing new, just repeated use of the model: price the call at each implied volatility, subtract the price paid and multiply by the number of options.

$$\text{profit now} = 100 \times (\text{new call price} - 5.00)$$

The only difference between holding and closing is *time*: the profit is the same in expectation, but holding for the full ten weeks exposes us to inputs being wrong. As the book says: "The longer a position is held, the greater the possibility of error from the inputs into the model."

## Common confusions
- **A loss now does not mean a bad trade.** An option trader, like any speculator, can rarely pick the exact top or bottom of implied volatility. A good position can become even better and show a temporary loss on the way.
- **Implied volatility is not the stock's volatility.** In the adverse case the stock's real volatility (what pays our adjustments) is unchanged at 37.62%; only the market's *price* for options changed.
- **Taking the profit early is not always possible.** It requires implied volatility to rise toward your forecast, which the market is under no obligation to do.
- **Why must we also trade the underlying when we close?** Because we are still short 50 contracts from the original hedge (plus whatever the adjustments left). Closing the options without buying them back leaves us with a naked directional position.

## Related
- Chapter: [[chapters/08-dynamic-hedging]]
- Previous: [[concepts/08-dynamic-hedging/realized-volatility-and-the-race]]
- Next: [[concepts/08-dynamic-hedging/futures-option-hedge-and-variation]]
- Earlier: [[concepts/06-volatility/implied-volatility]], [[concepts/07-risk-measurement-i/vega]]
- Code: [[code/dynamic_hedging.ipynb]]
- See also: [[glossary]], [[formulas]]
