# Summary tables: where each measure is largest (Figures 9-25 and 9-26)

**One-line definition:** the chapter ends with two reference tables: the traditional risk measures (delta, lambda, gamma, theta, vega, rho) and the nontraditional higher-order ones (vanna, charm, speed, color, volga, vega decay, zomma), each with the conditions in which it is **maximised**.

## Intuition
There are too many risk measures to watch all the time. These tables tell you **where to look**: for each measure, in what kind of option and in what kind of market is it biggest? Gamma, theta and vega share a home: at the money.

## The maths: the book's two tables
Symbols in both: $C$ call value, $P$ put value, $S$ underlying price, $t$ time to expiration, $\sigma$ annual volatility, $r$ domestic interest rate, $r_f$ foreign rate (or dividend yield). $\partial$ is a *partial derivative* ("change in one input, the others fixed", [[00-maths-refresher/derivatives-and-rates-of-change]]).

**Figure 9-25: traditional measures**

| Measure | Sensitivity of the... | To a change in... | Math | Maximized when |
|---|---|---|---|---|
| Delta ($\Delta$) | theoretical value (points) | underlying price (points) | $\partial C/\partial S$; $\;\partial C/\partial S \approx \partial P/\partial S + 1$ | deeply in the money |
| Lambda ($\Lambda$ or $\Omega$), elasticity | theoretical value (percent) | underlying price (percent) | $\Delta_c \times S/C$; $\;\Delta_p \times S/P$ | out of the money, close to expiration, low volatility |
| Gamma ($\Gamma$), curvature | delta | underlying price | $\partial^2 C/\partial S^2 = \partial^2 P/\partial S^2$ | at the money, close to expiration, low volatility |
| Theta ($\Theta$), time decay | theoretical value | time to expiration | $\partial C/\partial t$; $\partial P/\partial t$ | at the money, close to expiration, low volatility |
| Vega | theoretical value | volatility | $\partial C/\partial \sigma = \partial P/\partial \sigma$ | at the money, long term |
| Rho ($P$) | theoretical value | interest rate | $\partial C/\partial r$; $\partial P/\partial r$ | deeply in the money, long term |
| Rho$_f$ or phi ($\Phi$) | theoretical value | foreign rate or dividend yield | $\partial C/\partial r_f$; $\partial P/\partial r_f$ | deeply in the money, long term |

**Figure 9-26: nontraditional higher-order measures**

| Measure | Sensitivity of the... | To a change in... | Math | Maximized when |
|---|---|---|---|---|
| Vanna | delta; vega | volatility; underlying price | $\partial^2 C/\partial S\,\partial\sigma = \partial^2 P/\partial S\,\partial\sigma$ | 15-20 and 80-85 delta; low volatility |
| Charm (delta decay) | delta; theta | time; underlying price | $\partial^2 C/\partial S\,\partial t$ | 15-20 and 80-85 delta; close to expiration |
| Speed | gamma | underlying price | $\partial^3 C/\partial S^3 = \partial^3 P/\partial S^3$; $\partial^2\Delta/\partial S^2$; $\partial\Gamma/\partial S$ | 15-20 and 80-85 delta; low volatility; close to expiration |
| Color (gamma decay) | gamma; charm | time to expiration; underlying price | $\partial^3 C/\partial S^2\,\partial t$; $\partial\Gamma/\partial t$ | at the money; close to expiration; low volatility |
| Volga (vomma) | vega | volatility | $\partial^2 C/\partial\sigma^2 = \partial^2 P/\partial\sigma^2$ | 10 and 90 delta; long term; low volatility |
| Vega decay | vega | time | $\partial^2 C/\partial\sigma\,\partial t$ | 20 and 80 delta; close to expiration |
| Zomma | gamma; vanna | volatility; underlying price | $\partial^3 C/\partial S^2\,\partial\sigma$; $\partial\Gamma/\partial\sigma$ | at the money; close to expiration; low volatility |

Notes on reading them:
- **Two entries in a cell** (for example "delta; vega") are the two equivalent readings of the same mixed derivative ([[00-maths-refresher/sensitivity-of-a-sensitivity]]).
- **Delta is "maximized" deeply in the money** only in the sense that a call's delta tends to 1 there.
- Vega decay is listed with vega's sensitivity to time; by the same mixed-derivative logic it is also theta's sensitivity to volatility (the book lists only the first reading).
- **The book's formulas differentiate with respect to time *to* expiration** ($t$), so its signs for the time-based ones (charm, color, vega decay) are the opposite of "change per day passing".

## Our check against a model
The notebook finds, for a 91-day option at 25% volatility, the call delta at which each measure is largest in size ([[code/risk_measures_ii.ipynb]]):

| Measure | Largest at call delta (ours) | Book | Where it crosses zero (ours) |
|---|---|---|---|
| Vanna | 17 and 86 | 15-20 and 80-85 | about 55 |
| Charm | 17 and 86 | 15-20 and 80-85 | about 55 |
| Volga | 8 and 93 | 10 and 90 | about 50 to 55 |
| Vega decay | 16 and 84 | 20 and 80 | never |
| Speed | 14 and 83 | 15-20 and 80-85 | about 45 |
| Color | at the money (52) | at the money | about 18 and 86 |
| Zomma | at the money (52) | at the money | about 17 and 86 |

These agree with the book. The crossings a little above or below 50 echo the book's footnote that vanna "is actually 0 for delta values slightly larger than 50". The crossings of color and zomma near 15-20 and 85 confirm the book's "close to 0" statement for deltas 15 and 85.

## The three questions to ask of any option
1. **Where is it?** (in, at or out of the money): at the money is where gamma, theta and vega are biggest.
2. **How long is left?** Close to expiration, at-the-money gamma and theta are big, vega is small.
3. **How volatile is the market?** Low volatility makes the at-the-money option's gamma and the in- and out-of-the-money options' sensitivities (vanna, speed, volga) bigger.

## Common confusions
- **"Maximized" refers to the size, not the sign.** Many of these change sign through the middle of the delta range.
- **Not every measure matters for every trade.** The book: "not every risk is important in every situation", but "it is almost impossible to overemphasize the importance of risk management in option trading".
- **Do not memorise.** Learn the rule, then derive: at the money $\to$ gamma, theta, vega; around 15-20 / 80-85 delta $\to$ the changes of delta and gamma; around 10 / 90 $\to$ volga.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Previous: [[concepts/09-risk-measurement-ii/lambda-leverage]]
- Start of the chapter's ideas: [[concepts/09-risk-measurement-ii/higher-order-sensitivities-and-their-names]]
- See also: [[glossary]], [[formulas]]
