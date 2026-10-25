# Interest rates and futures options, and currency options

**One-line definition:** the effect of interest rates on an option depends on whether the underlying is a stock, a futures contract or a foreign currency, and on whether premium is paid up front (stock-type) or marked daily (futures-type).

## Futures options
Settlement matters here ([[concepts/01-financial-contracts/settlement-margin-and-variation]]).

**Futures-type settlement** (common outside the US): no money changes hands when the option *or* the futures contract is traded. Interest rates affect neither the forward price (the futures price already is the forward) nor the present value. So both calls and puts are **insensitive** to rate changes: rho $= 0$.

**Stock-type settlement** (US futures options): the premium is paid up front. The forward price is unchanged by interest rates, but the option's present value falls when rates rise. So **both calls and puts fall**. The effect is usually small, because the option is worth much less than the underlying, unless it is very deeply in the money. Futures options are much less rate-sensitive than stock options.

## Foreign-currency options
Here the option value depends on **two** rates. For a spot exchange rate $S$, domestic rate $r_d$, foreign rate $r_f$, time $t$ (from Chapter 2):

$$F = S \times \frac{1 + r_d\,t}{1 + r_f\,t}$$

- **Foreign rate up:** the denominator grows, $F$ falls. Calls fall, puts rise.
- **Domestic rate up:** the numerator grows, $F$ rises. For options with stock-type settlement the present value also falls, but as with stock options the forward-price effect dominates. Calls rise, puts fall.

(This is for options on the *actual* currency; options on currency futures behave like any futures option.)

## Summary (Figure 7-2)

| | Domestic rate up | Domestic rate down | Foreign rate up | Foreign rate down |
|---|---|---|---|---|
| Stock option calls | rise | fall | n/a | n/a |
| Stock option puts | fall | rise | n/a | n/a |
| Futures option calls, stock-type | fall | rise* | n/a | n/a |
| Futures option puts, stock-type | fall | rise* | n/a | n/a |
| Futures options, futures-type | no effect | no effect | n/a | n/a |
| Currency option calls | rise | fall | fall | rise |
| Currency option puts | fall | rise | rise | fall |

*In the project PDF the table appears to show "fall, fall" for futures options under stock-type settlement. By the logic in the text (only discounting matters), a rate *fall* must raise the value, so the second "fall" looks like a misprint.

## Worked example
Futures option (stock-type), futures 100, strike 100, one year, volatility 25%: the call is worth 9.462 at a 5% rate and 9.368 at 6%. The put falls by the same amount (they have the same value at the money-forward). Our model check: [[code/risk_measures.ipynb]].

## Common confusions
- **No effect does not mean zero risk to the trader.** Funding costs of the *futures margin* are a separate matter.
- **Which currency is "domestic"?** The currency in which the option price is paid.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/rho]]
- See also: [[concepts/02-forward-pricing/forward-price-by-instrument]], [[glossary]], [[formulas]]
