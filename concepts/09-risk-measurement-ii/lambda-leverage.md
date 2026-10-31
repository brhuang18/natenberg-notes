# Lambda (elasticity or leverage)

**One-line definition:** lambda ($\Lambda$) is the **percentage** change in an option's value for a 1% change in the underlying price: delta (as a decimal) multiplied by the underlying price over the option's theoretical value.

## Intuition
Delta says how many *points* the option gains per point in the underlying. But a 1-point rise means different things for a 4.00 option and a 100 underlying. Lambda asks the question an investor with a fixed amount of money would ask: "For each 1% the underlying moves, what percent does my **option investment** move?" If the answer is 5, the option has five times the percentage swing of the underlying: it is a **leveraged** way to hold the same exposure. Traders sometimes call lambda the option's "leverage value".

Another way to see it: an option with a delta of 0.20 behaves like owning 0.20 of one underlying unit, which is exposure worth $0.20 \times 100 = 20$. It costs 4.00. So 4.00 buys 20 of exposure, and the leverage is $20/4.00 = 5$.

## The maths
$$\Lambda = \Delta \times \frac{S}{TV}$$

- $\Delta$: delta as a **decimal** (0.20, not 20).
- $S$: underlying price. $TV$: option theoretical value.
- Why this formula: percentage change in option divided by percentage change in underlying is $\dfrac{\Delta TV / TV}{\Delta S / S} = \dfrac{\Delta TV}{\Delta S} \times \dfrac{S}{TV}$, and $\Delta TV / \Delta S$ is just the delta ([[00-maths-refresher/proportionality-and-percentage-change]]).
- Calls have positive lambda and puts have negative lambda, because lambda is built from the delta (which carries the sign).

## Worked example (the book's)
Call worth 4.00, delta 20, underlying 100.
- Underlying rises one point to 101: a 1% rise ($1/100$).
- Option rises about $0.20$ to about 4.20 (the book writes "new delta" here; it means new *value*): a 5% rise ($0.20/4.00$).
- Lambda $= 0.20 \times 100/4.00 = 5$. ✓

**More numbers (our model, underlying 100, no interest, [[code/risk_measures_ii.ipynb]]):**

| Call | Value | Delta | Lambda |
|---|---|---|---|
| 90 strike, 91 days, volatility 25% | 11.31 | 81.8 | 7.2 |
| 100 strike | 4.98 | 52.5 | 10.5 |
| 110 strike | 1.68 | 24.2 | 14.4 |
| 110 strike, volatility 15% | 0.38 | 10.8 | 28.6 |
| 110 strike, volatility 40% | 4.28 | 35.3 | 8.2 |
| 110 strike, 30 days | 0.32 | 9.8 | 30.5 |
| 110 strike, 7 days | 0.003 | 0.3 | 96 |

Put lambdas for the same setting (91 days, volatility 25%): the 90 put $-13.9$, the 100 put $-9.5$, the 110 put $-6.5$.

![Lambda of calls and puts as the underlying changes](../../images/ch09-lambda.png)

## What to remember
- **Largest for out-of-the-money options.** Cheap options have a small value in the denominator, so lambda is big. As the underlying rises, call lambdas decline and put lambdas rise in size (the put becomes more out of the money).
- **Falls when volatility rises, rises when volatility falls or time passes** (in size, for puts).
- **To maximise percentage return** on a given investment, compared with an equal investment in the underlying: trade out-of-the-money options close to expiration in a low-volatility environment. The book adds, "Of course, this is true only in theory": bid-ask spreads and thin liquidity can make a big lambda position impractical compared with the underlying itself.
- **Not widely used.** The book says lambda "is not a widely used risk measure".

## Common confusions
- **Lambda is not delta.** Delta 0.20 and lambda 5 are the *same* exposure measured two ways, points versus percent.
- **Put lambdas are negative, "falling" means bigger negative.** The book says lambda values for both calls and puts "fall" if volatility increases; for puts that means *shrinking in size* (the numbers get closer to zero). See the right panel of the figure.
- **High lambda is not high return.** It magnifies losses as well. A lambda of 96 (the 7-day call) means a 1% adverse move in the underlying removes roughly 96% of the premium (for small moves; the estimate is rough at that size).
- **Lambda is sometimes written omega ($\Omega$)** in the book's summary table.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/proportionality-and-percentage-change]]
- Previous: [[concepts/09-risk-measurement-ii/short-dated-at-the-money-options-the-riskiest]]
- Next: [[concepts/09-risk-measurement-ii/summary-tables-where-each-measure-is-largest]]
- Built on: [[concepts/07-risk-measurement-i/delta]]
- See also: [[glossary]], [[formulas]]
