# Volatility as a standard deviation (and the forward price as the mean)

**One-line definition:** when you type a volatility into a pricing model you are typing a standard deviation. Our working definition: *volatility is the one-standard-deviation price change, in percent, over one year*, and the distribution is centred on the **forward price**.

## Intuition
Chapter 5's simple approach needed a list of prices and probabilities. A normal distribution gives us all of them from just two numbers:

| Model needs | Number | Source |
|---|---|---|
| Centre of the distribution | **mean** | the forward price of the underlying |
| Width of the distribution | **standard deviation** | the volatility $\sigma$ |

Traders just say "volatility" instead of "standard deviation", and use the Greek letter sigma, $\sigma$.

## Why the mean is the forward price, not today's price
In Chapter 5 we saw that the average outcome must equal the forward price in an arbitrage-free market ([[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]]). If the forward price is the mean, then in the long run any trade made at the current underlying price will just break even.

The model takes the current price, time to expiration, interest rates, and (for stocks) dividends, computes the forward price, and makes that the mean. The different forms of Black-Scholes differ mainly in how they calculate the forward price.

## The maths
Volatility $\sigma$ is annual, in percent. A one-standard-deviation price change over one year is

$$\sigma \times F$$

and the likely range one year ahead is

$$F \pm k\,(\sigma F), \qquad k = 1: \text{about } 68\%, \quad k = 2: \text{about } 95\%, \quad k = 3: \text{about } 99.7\%$$

- $F$ = forward price (the mean)
- $\sigma$ = annual volatility as a decimal (20% is $0.20$)
- $k$ = number of standard deviations

## Worked example 1: contract with a forward price of 100, volatility 20%
One standard deviation is $20\% \times 100 = 20$.

| Standard deviations | Range one year from now | Chance the price is inside |
|---|---|---|
| 1 | $100 \pm 20$: 80 to 120 | about 68% |
| 2 | $100 \pm 40$: 60 to 140 | about 95% |
| 3 | $100 \pm 60$: 40 to 160 | about 99.7% |

## Worked example 2: stock at 100, volatility 20%, interest 8%, no dividend
We are given the **current** price, so find the forward price first:

$$F = 100 \times (1 + 0.08 \times 1) = 108$$

One standard deviation is $20\% \times 108 = 21.60$ (not $20\% \times 100$).

| Standard deviations | Range | Chance |
|---|---|---|
| 1 | $108 \pm 21.60$: 86.40 to 129.60 | about 68% |
| 2 | $108 \pm 43.20$: 64.80 to 151.20 | about 95% |
| 3 | $108 \pm 64.80$: 43.20 to 172.80 | about 99.7% |

The distribution is centred on 108, not 100.

## Unlikely is not impossible
Back to the forward-100, 20% example. A year later the contract trades at 35. Was 20% wrong?

1. Distance from the mean: $35 - 100 = -65$.
2. In standard deviations: $-65 / 20 = -3.25$.
3. Chance of finishing that low or lower (one tail): about 0.058%, roughly **1 chance in 1,700** (the book says "less than one chance in 1,500").

Rare, but possible. Compare 15 heads in 15 flips of a fair coin: $1/2^{15} = 1$ chance in 32,768 (the book says "less than one chance in 32,000"), and it can happen. You cannot condemn a volatility from one observation; you need a *large number* of price changes to see the real distribution ([[concepts/06-volatility/checking-volatility-against-price-changes]]).

## Common confusions
- **The percentage applies to the forward price, not the spot price.** For a stock with positive interest rates the forward is higher.
- **Volatility is a percentage of price.** The same 20% means a bigger dollar spread for a 200 stock than for a 50 stock.
- **This is the book's "working definition"**: it says it will modify it slightly later (the lognormal version, [[concepts/06-volatility/lognormal-distributions]]).

## Related
- Chapter: [[chapters/06-volatility]]
- Maths needed: [[00-maths-refresher/normal-distribution-and-z-scores]], [[00-maths-refresher/simple-interest-and-time-fractions]]
- Previous: [[concepts/06-volatility/mean-and-standard-deviation]]
- Next: [[concepts/06-volatility/scaling-volatility-for-time]]
- Forward price: [[concepts/02-forward-pricing/forward-price-cost-and-benefit]]
- See also: [[glossary]], [[formulas]]
