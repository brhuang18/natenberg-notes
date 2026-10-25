# The riskless hedge and the hedge ratio

**One-line definition:** a riskless hedge is a position in the underlying chosen so that, for small price moves, it gains or loses exactly as much as your option position, in the opposite direction. The number of underlying contracts needed per option is the **hedge ratio**.

## Intuition
Suppose you buy a call because the market says it is cheap compared with its theoretical value. You do not really want to bet on the stock going up; you want to collect the mispricing. So you strip out the directional bet by taking an *opposite* position in the underlying. If the stock rises, the call gains and your short stock loses about the same; if it falls, the reverse. What is left is the pricing edge.

Why must the hedge be *adjusted* as the market moves? In the simple approach, an option's value depends on the probabilities of different prices. Those probabilities change when the underlying moves: if the stock is at 100 and we give 25% to a price of 120, and the stock then falls to 90, we might cut that chance to 10%. Re-balancing the hedge as prices move is how the trader allows for these shifting probabilities (this is **dynamic hedging**, Chapter 8).

## An option as a substitute for the underlying
- A **call** behaves like a *long* position in the underlying.
- A **put** behaves like a *short* position in the underlying.

Whether the option is a *better* substitute than the underlying itself depends on theoretical value versus market price:

| If... | ...then, in the long run, it is more profitable to |
|---|---|
| a call costs *less* than its theoretical value, or a put can be *sold* for more than its value | go long via options (buy calls / sell puts) rather than buy the underlying |
| a put costs *less* than its theoretical value, or a call can be *sold* for more than its value | go short via options (buy puts / sell calls) rather than sell the underlying |

## The four basic positions and their hedges

| Option position | Acts like | Hedge with |
|---|---|---|
| Buy calls | Long the underlying | **Sell** underlying |
| Sell calls | Short the underlying | **Buy** underlying |
| Buy puts | Short the underlying | **Buy** underlying |
| Sell puts | Long the underlying | **Sell** underlying |

**Memory rule (from the book):**
- With **calls**, do the *opposite* in the underlying: buy calls, sell underlying; sell calls, buy underlying.
- With **puts**, do the *same*: buy puts, buy underlying; sell puts, sell underlying.

Why: the hedge must offset the position, so it is simply "the opposite of what the option acts like". A bought put acts short, so the hedge is *long* underlying. New traders often get puts backwards, buying puts *and* selling the underlying. That is no hedge: both legs lose when the stock rises, and both gain when it falls.

## How many underlying contracts? The hedge ratio
The right amount is the option's **hedge ratio**: the number of underlying contracts that moves like one option for small price changes. The book only names it here and develops it later as the **delta** (Chapter 7). As a foretaste, from the chapter on spreading: a call with a delta of 25 means roughly 0.25 of an underlying contract per call, so selling four such calls is hedged by buying about one underlying contract.

## Worked example
You buy 1 call that the model says is cheap.
1. Position acts like long underlying, so the hedge is to **sell** underlying.
2. Stock rises 1 point: call gains by about (hedge ratio) points, short stock loses 1 point per contract sold. With the right amount these cancel.
3. Stock falls 1 point: the opposite. The hedge works only for *small* moves, which is why it has to be re-adjusted.

## Common confusions
- **"Riskless" is for small moves only.** Big moves, changes in volatility and time passing still change the value.
- **Calls: opposite. Puts: same.** Check it against the table before trading.
- **The hedge captures the mispricing, not a view.** You hedge because you want the theoretical edge, not a bet on direction.

## Related
- Chapter: [[chapters/05-theoretical-pricing-models]]
- Previous: [[concepts/05-theoretical-pricing-models/black-scholes-model-and-inputs]]
- Next: [[concepts/05-theoretical-pricing-models/choosing-the-inputs]] (the underlying price to use depends on the hedge trade)
- Earlier: [[concepts/04-expiration-profit-and-loss/equivalent-positions]] (calls and puts as long/short stand-ins)
- See also: [[glossary]]
