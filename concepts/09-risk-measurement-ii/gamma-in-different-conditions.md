# Gamma in different conditions

**One-line definition:** gamma is largest at the money, falls at higher exercise prices (the opposite of theta and vega), and for an at-the-money option it **rises as time passes or volatility falls**; in and out of the money it tends to move the other way.

## Intuition
Gamma says how fast delta changes. The key idea: **delta changes fastest where the outcome is still undecided, i.e. at the money**, and how fast depends on how undecided it is.
- **Lots of time or high volatility:** even an at-the-money option's delta stays near 50 (a wide range of outcomes is possible). Small moves hardly change delta, so gamma is low.
- **Little time or low volatility:** the market will probably end very close to where it is. Whether the strike gets crossed is decided by a small move, so delta swings quickly from near 0 to near 100 across the strike: gamma is high.

*"Gamma, theta and vega are greatest when an option is at the money."* That is why at-the-money options are the most actively traded in most markets: they offer the characteristics traders come for.

## The maths and the patterns
![Gamma against the underlying price, time and volatility](../../images/ch09-gamma-profiles.png)

**1. Against the underlying price (Figure 9-18).** A hump around the exercise price. The hump peaks slightly **below** the strike (about 97.7 for a 100 strike, 91 days, volatility 25% in our model; the book does not mention this, it follows from the lognormal shape). Unlike theta and vega, **at-the-money gamma gets smaller at higher exercise prices**: gamma is inversely proportional to the strike ([[concepts/09-risk-measurement-ii/at-the-money-scaling-with-the-exercise-price]]).

**2. The key example: why at the money gamma rises as time passes or volatility falls (Figure 9-20).** A 100 call with the underlying at 97.50, so it is out of the money and its delta is below 50. Move the underlying up 5 points to 102.50 and watch the delta:

| Case | Delta at 97.50 | Delta at 102.50 | Approximate gamma |
|---|---|---|---|
| Little time or low volatility | 25 | 75 | $\dfrac{75 - 25}{102.50 - 97.50} = \dfrac{50}{5} = 10$ |
| Lots of time or high volatility | 45 | 55 | $\dfrac{55 - 45}{102.50 - 97.50} = \dfrac{10}{5} = 2$ |

*How to read it.* "Approximate gamma" is just the change in delta divided by the change in the underlying (deltas per point). The same move produces five times the change in delta in the first case.

Our model (no interest, [[code/risk_measures_ii.ipynb]]) reproduces both: volatility 20% with 13 days left gives deltas 25.7 and 75.0 (gamma about 9.9); volatility 40% with 91 days left gives 48.9 and 58.8 (gamma about 2.0). (The second has deltas a little above 45 and 55 because the model's at-the-money delta sits above 50; the gamma of 2 matches.)

**3. In and out of the money, the effect reverses.** The book's general rule: gamma **falls** if we reduce volatility and **rises** if we increase it, for in- and out-of-the-money options. Underlying 100, gamma at 91 days:

| Volatility | 90 call | 100 call | 110 call |
|---|---|---|---|
| 10% | 0.82 | 7.99 | 1.35 |
| 15% | 1.88 | 5.32 | 2.48 |
| 25% | 2.12 | 3.19 | 2.50 |
| 40% | 1.64 | 1.99 | 1.86 |
| 60% | 1.17 | 1.32 | 1.31 |

and with time passing (volatility 25%):

| Days left | 90 call | 100 call | 110 call |
|---|---|---|---|
| 365 | 1.37 | 1.58 | 1.54 |
| 180 | 1.79 | 2.26 | 2.05 |
| 91 | 2.12 | 3.19 | 2.50 |
| 30 | 1.79 | 5.56 | 2.41 |
| 14 | 0.76 | 8.15 | 1.28 |
| 7 | 0.11 | 11.52 | 0.27 |
| 3 | 0.00 | 17.60 | 0.00 |
| 1 | 0.00 | 30.49 | 0.00 |

The at-the-money column rises monotonically as time passes (and falls as volatility rises), exactly as stated. The out- and in-the-money columns first rise, then collapse. The book's footnote 7 covers this: "this is a general rule", and an option only slightly in or out of the money can act like an at-the-money one, depending on volatility and time. A 10%-away option at 60% volatility acts like an at-the-money option (gamma 1.31 vs 1.32).

**4. Link with theta.** Because gamma and theta are closely related ([[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]]), graphing an at-the-money option's gamma against time gives a curve like the theta-against-time curve (Figure 9-10): flat early, then climbing steeply near expiration.

## Worked example
At the money, 100 underlying, volatility 25%. Moving from 91 days to 30 days to 7 days: gamma $3.19 \to 5.56 \to 11.52$. A 1-point move in the underlying changes the delta by about 3, then 6, then 12 points. Since position gamma adds across options, 100 long 7-day calls have a gamma of $100 \times 11.52 = 1{,}152$ deltas per point: after one point of movement your delta has changed by 1,152, the equivalent of about 11.5 underlying contracts. **The same position, with the same options, carries about 3.6 times the gamma risk it did with 91 days left** ($11.52/3.19$).

## Common confusions
- **Gamma is big when theta is big, for at-the-money.** The two grow together as expiration nears ([[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]]).
- **"Highest at the money" is for fixed time and volatility.** Compare options at one strike, not across different expirations.
- **Theta and vega rise with the exercise price at the money; gamma falls.** All three are one fact about percentages.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Previous: [[concepts/09-risk-measurement-ii/volga-and-vega-decay]]
- Next: [[concepts/09-risk-measurement-ii/speed-color-and-zomma]]
- Built on: [[concepts/07-risk-measurement-i/gamma]], [[concepts/08-dynamic-hedging/gamma-and-the-unhedged-amount]]
- See also: [[concepts/09-risk-measurement-ii/short-dated-at-the-money-options-the-riskiest]], [[glossary]], [[formulas]]
