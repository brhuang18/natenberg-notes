# The Black-Scholes model and its five inputs

**One-line definition:** Black-Scholes is the standard option pricing model. Feed it five numbers (exercise price, time to expiration, underlying price, interest rate, volatility) and it returns a theoretical value, using the same idea as our simple approach but with a full, continuous set of price outcomes.

## Intuition
Our five-price example needed us to invent probabilities by hand. Black-Scholes does the equivalent automatically: from the inputs it builds a smooth probability distribution over *every* possible price at expiration, centred on the forward price, and computes the option's discounted expected value. The details of that distribution come in Chapter 6 (volatility) and the formula itself later; here we only need the inputs and where the model came from.

## A short history (as the book tells it)
| Year | Who | What |
|---|---|---|
| 1877 | Charles Castelli | Pamphlet describing hedging and trading strategies, e.g. the "call-of-more" (now a covered write) and the "call-and-put" (now a straddle) |
| 1900 | Louis Bachelier | *The Theory of Speculation*: first use of higher mathematics to price options. Little practical use: no organised option markets yet |
| 1973 | Fischer Black and Myron Scholes (Robert Merton did related work) | The first practical pricing model, published as the Chicago Board Options Exchange opened. Easy arithmetic, few inputs, mostly observable: ideal for traders in the new market |
| Shortly after 1973 | Black and Scholes | Added a dividend component for stocks that pay dividends |
| 1976 | Fischer Black | Version for options on **futures** (the *Black model*) |
| 1983 | Mark Garman and Steven Kohlhagen | Version for options on **foreign currencies** (the *Garman-Kohlhagen model*) |

Original Black-Scholes was for **European** options on **non-dividend-paying stocks**. All the later versions are so similar that they are all just called "Black-Scholes". They differ only in:
1. how they calculate the **forward price** of the underlying, and
2. the **settlement procedure** of the option (stock-type or futures-type).

A trader simply picks the version that matches the option and underlying.

## The five inputs

```
exercise price ──┐
time to expiry ──┤
underlying price ┼──> [ pricing model ] ──> theoretical value
interest rate ───┤
volatility ──────┘
```

| # | Input | Known for certain? | Where to read more |
|---|---|---|---|
| 1 | Exercise price $X$ | Yes: fixed by the contract | [[concepts/05-theoretical-pricing-models/choosing-the-inputs]] |
| 2 | Time to expiration $t$ | Yes: the expiry date is fixed | same |
| 3 | Underlying price $S$ | Not obvious: bid, ask, last trade? | same |
| 4 | Interest rate $r$ | Judgement: which rate? | same |
| 5 | Volatility | **No**: must be estimated | Chapter 6 |

For stock options a dividend estimate is also needed, but dividends only matter by changing the forward price, so the book does not count them as a separate input. Foreign-currency options need **two** interest rates (domestic and foreign).

Only *volatility* is a genuine unknown. The first four can be read off a screen or contract; volatility is a guess about the future speed of the market, and it often decides the trade.

## Black and Scholes' second idea: the riskless hedge
The model does not stop at a value. It also tells you *how to hedge*: hold an offsetting position in the underlying so small price moves cancel. Why that matters is in [[concepts/05-theoretical-pricing-models/riskless-hedge-and-hedge-ratio]].

## Common confusions
- **Black-Scholes is not one formula for everything.** There are variants (Black, Garman-Kohlhagen); they are all "Black-Scholes" to traders, but they handle the forward price and settlement differently.
- **"Original" Black-Scholes is European only.** Early exercise of American options needs more work (Chapter 16 and alternative models).
- **The model gives a value, not a price.** Compare it with the market price to decide whether to trade.
- **Put values** come from the same logic as call values, or from the call value through a fixed relationship between a European call, put and underlying that the book covers later (put-call parity).

## Related
- Chapter: [[chapters/05-theoretical-pricing-models]]
- Previous: [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]]
- Next: [[concepts/05-theoretical-pricing-models/riskless-hedge-and-hedge-ratio]]
- Forward price per instrument: [[concepts/02-forward-pricing/forward-price-by-instrument]]
- European vs American: [[concepts/03-contract-specifications-and-option-terminology/european-vs-american-exercise]]
- See also: [[glossary]], [[formulas]]
