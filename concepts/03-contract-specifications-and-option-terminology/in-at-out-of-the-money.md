# In, at and out of the money

**One-line definition:** an option is **in the money** if it has positive intrinsic value, **out of the money** if it has none, and **at the money** if its exercise price equals the underlying price.

## Intuition
The labels say whether exercising right now would pay. A call is a right to buy, so it is "in the money" when you could buy *below* the market. A put is a right to sell, so it is "in the money" when you could sell *above* the market.

## The rules
Let $S$ be the underlying price and $X$ the exercise price.

| Option | In the money | At the money | Out of the money |
|---|---|---|---|
| Call | $X < S$ | $X = S$ | $X > S$ |
| Put | $X > S$ | $X = S$ | $X < S$ |

"In the money **by**" means by the amount of intrinsic value. An out-of-the-money option has no intrinsic value, so its price is all time value ([[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]]).

For the same underlying and exercise price, if the call is in the money, the put is out of the money, and vice versa.

## Worked example (the book's)
Stock at \$44:

| Option | Status | Amount |
|---|---|---|
| \$40 call | in the money | by $44 - 40 = 4$ |
| \$55 put | in the money | by $55 - 44 = 11$ |
| \$40 put | out of the money | by $44 - 40 = 4$ |
| \$55 call | out of the money | by $55 - 44 = 11$ |

On a strike ladder, calls with strikes **below** the current price are in the money, and puts with strikes **above** it are in the money.

## At the money
- Strictly, at the money means $X = S$ exactly. Such an option has no intrinsic value, so technically it is also out of the money. Traders still keep "at the money" as its own label because at-the-money options often have special, desirable characteristics (explored later) and are the most actively traded.
- On an exchange, "at the money" in practice means the **call and put whose strike is closest to the underlying price**.

**Example (the book's).** Stock at \$74, strikes every \$5 (65, 70, 75, 80). The **75 call and 75 put** are the at-the-money options.

Careful with what that means under the strict definitions: at \$74, the 75 call has intrinsic value $\max(0, 74 - 75) = 0$, while the 75 put has $\max(0, 75 - 74) = 1$. So by convention both are "at the money", though strictly the put is in the money by 1.

The book later introduces options *at the forward* (strike equal to the forward price), which are often the actively traded benchmark ([[chapters/02-forward-pricing]]).

## Common confusions
- **Not the same as profitable.** "In the money" does not mean you have made money; you may have paid more for the option than its intrinsic value.
- A put is in the money when the market is *below* the strike. The direction is the opposite of a call.

## Related
- Chapter: [[chapters/03-contract-specifications-and-option-terminology]]
- See also: [[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]], [[glossary]]
