# Time and volatility have similar effects

**One-line definition:** more time to expiration acts like higher volatility, and less time acts like lower volatility, so if you cannot tell what a change in one does to an option, ask what the other would do.

## Intuition
An option cares about **how far the underlying might wander before expiration**. Two things set that distance: how fast it moves (volatility) and how long it has to move (time). A wild market for one month and a calm market for four months can allow the same wandering. So the two inputs can stand in for each other.

The book uses this as a rule of thumb: "More time, like higher volatility, increases the likelihood of large price changes. Less time, like lower volatility, reduces the likelihood of large price changes."

## The maths
From Chapter 6, the spread of price changes grows with the square root of time ([[concepts/06-volatility/scaling-volatility-for-time]]):

$$\sigma_t = \sigma_{\text{annual}} \times \sqrt{t}$$

In the model, with no interest, volatility and time enter the option value **only through this one product**, $\sigma\sqrt{t}$. Two combinations with the same $\sigma\sqrt{t}$ give the same option value, delta, and gamma-per-point-of-value.

- Step 1: compute $\sigma\sqrt{t}$ for each case (with $t$ in years).
- Step 2: if equal, the options are equivalent.

## Worked example
A 110 call, underlying 100 (no interest, from [[code/risk_measures_ii.ipynb]]):

| Volatility | Days to expiration | $\sigma\sqrt{t}$ | Call value | Delta |
|---|---|---|---|---|
| 25% | 91 | $0.25 \times \sqrt{91/365} = 0.1248$ | 1.676 | 24.16 |
| 50% | 22.75 | $0.50 \times \sqrt{22.75/365} = 0.1248$ | 1.676 | 24.16 |
| 12.5% | 364 | $0.125 \times \sqrt{364/365} = 0.1248$ | 1.676 | 24.16 |

Doubling volatility to 50% does exactly what cutting time to one quarter does to the *spread*, and quadrupling time to a year while halving volatility does too. This explains why the pictures in the chapter for "more volatility" and "more time" look alike:

| Effect | Raising volatility | Adding time |
|---|---|---|
| Call deltas | move toward 50 | move toward 50 |
| At-the-money gamma | falls | falls |
| Vega and gamma in/out of the money | tend to rise | tend to rise |
| Option value | rises | rises |

## Common confusions
- **Same *picture*, not same *derivative*.** Theta and vega are different measures: one is the effect of time and the other the effect of volatility. They agree in direction in the cases above, not in size.
- **It works exactly only without interest.** With interest rates and dividends, time also moves the forward price, which volatility does not do. The rule is a guide.
- **Time moves by itself; volatility does not.** A position's risk changes every day as time passes, whether or not anything else happens ([[concepts/09-risk-measurement-ii/vanna-and-charm]]).

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/standard-deviation-and-variance]], [[00-maths-refresher/proportionality-and-percentage-change]]
- Previous: [[concepts/09-risk-measurement-ii/higher-order-sensitivities-and-their-names]]
- Next: [[concepts/09-risk-measurement-ii/delta-changes-with-volatility-and-time]]
- See also: [[concepts/06-volatility/volatility-and-option-values]], [[glossary]], [[formulas]]
