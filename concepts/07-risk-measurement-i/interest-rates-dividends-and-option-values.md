# Interest rates and dividends: how they move stock option values

**One-line definition:** for stock options, higher interest rates raise call values and lower put values; higher dividends lower call values and raise put values. Both work through the forward price.

## Intuition
Interest rates touch an option in **two** ways, and they pull in opposite directions for a call:

1. **The forward price changes.** A stock bought today must be financed, so the forward price is the stock price plus interest, minus dividends: $F = S(1 + rt) - D$ ([[concepts/02-forward-pricing/forward-price-by-instrument]]). Raise the rate and $F$ rises. The option's value is built on the forward price ([[concepts/06-volatility/volatility-as-a-standard-deviation]]), so a higher $F$ lifts calls and lowers puts.
2. **The present value changes.** Under stock-type settlement the option is paid for today but pays off at expiration, so its value is discounted: $\text{value} = \dfrac{E}{1 + rt}$ ([[00-maths-refresher/present-value-and-discounting]]). Raise the rate and the discount is bigger, which lowers both calls and puts.

| | Forward-price effect | Present-value effect | Net |
|---|---|---|---|
| Call | up (helps) | down (hurts) | **rises** |
| Put | down (hurts) | down (hurts) | **falls** |

For the put, both effects push the same way, so the answer is clear. For the call they fight, and the forward-price effect wins.

## Why the forward-price effect wins
The forward-price effect applies to the whole **stock** price (large). The discount effect applies only to the **option** price (small). The stock is always worth more than an option on it.

Illustration (our numbers, stock 100, one-year at-the-money option, volatility 25%, interest rate moves from 5% to 6%):

| Step | Call | Put |
|---|---|---|
| Forward price rises by about $100 \times 0.01 = 1.00$; option moves by about delta times that | $+0.63$ (delta 0.63) | $-0.37$ (delta $-0.37$) |
| Discounting: option value (12.3 call, 7.5 put) loses about 1% of itself | $-0.12$ | $-0.07$ |
| **Net** | **about +0.51** | **about $-0.44$** |

The model gives $+0.509$ for the call and $-0.437$ for the put. Check with [[code/risk_measures.ipynb]].

## Dividends
A dividend is paid to the *stock holder*, not the option holder, so it lowers the forward price: $F = S(1 + rt) - D$. A bigger dividend gives a lower $F$, so calls fall and puts rise. A smaller dividend does the reverse.

| | Dividend raised | Dividend cut |
|---|---|---|
| Stock option calls | fall | rise |
| Stock option puts | rise | fall |

(Figure 7-3.) An interest rate rise and a dividend cut both lift the forward price, so they push option values the same way.

## Common confusions
- **"Higher rates always lower option values."** Only the present-value effect does that. For a stock call the forward-price effect dominates.
- **Why is the put clearly negative?** Both effects reduce it. A put is a right to *sell*; a higher forward price makes the right to sell at a fixed price less valuable.
- **Futures options and currency options behave differently.** See [[concepts/07-risk-measurement-i/futures-and-currency-options-interest-rates]].
- **The rate that matters depends on your hedge.** See [[concepts/07-risk-measurement-i/long-vs-short-stock-and-option-values]].

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/05-theoretical-pricing-models/choosing-the-inputs]]
- Next: [[concepts/07-risk-measurement-i/rho]]
- See also: [[glossary]], [[formulas]]
