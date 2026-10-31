# Sensitivity of a sensitivity: orders and mixed derivatives

**One-line summary:** delta, vega and theta are first-order sensitivities of an option's value. A "sensitivity of a sensitivity" (gamma, vanna, charm, volga...) is second order, and "the sensitivity of gamma" is third order. The **order** is how many times the value has been differentiated, and when two different inputs are involved the order of differentiation does not matter.

Used in: [[concepts/09-risk-measurement-ii/higher-order-sensitivities-and-their-names]], [[concepts/09-risk-measurement-ii/vanna-and-charm]], [[chapters/09-risk-measurement-ii]]

## Intuition
Think of the option value $V$ as a landscape that depends on three things you can change: the underlying price $S$, volatility $\sigma$ and time $t$. Standing at one spot you can ask "how steep is the ground if I walk in the $S$ direction?" That is delta. Then you can ask "as I step in the $\sigma$ direction, does that steepness change?" That is a sensitivity of a sensitivity (delta's sensitivity to volatility, called vanna). Nothing new in kind: just one more "how much does it change when..." question stacked on top.

## The maths
Write $V(S, \sigma, t)$ for the option value. Each first-order measure is a partial derivative ([[00-maths-refresher/derivatives-and-rates-of-change]]):

$$\Delta = \frac{\partial V}{\partial S} \qquad \text{vega} = \frac{\partial V}{\partial \sigma} \qquad \Theta = \frac{\partial V}{\partial t}$$

Differentiate a *second* time and you get the second-order measures; a *third* time, the third-order ones.

| Order | Symbol | Meaning in words | Name |
|---|---|---|---|
| 2 | $\dfrac{\partial^2 V}{\partial S^2}$ | delta's sensitivity to the underlying price | gamma |
| 2 | $\dfrac{\partial^2 V}{\partial S\,\partial \sigma}$ | delta's sensitivity to volatility | vanna |
| 2 | $\dfrac{\partial^2 V}{\partial S\,\partial t}$ | delta's sensitivity to time | charm |
| 2 | $\dfrac{\partial^2 V}{\partial \sigma^2}$ | vega's sensitivity to volatility | volga (vomma) |
| 2 | $\dfrac{\partial^2 V}{\partial \sigma\,\partial t}$ | vega's sensitivity to time | vega decay |
| 3 | $\dfrac{\partial^3 V}{\partial S^3}$ | gamma's sensitivity to the underlying price | speed |
| 3 | $\dfrac{\partial^3 V}{\partial S^2\,\partial t}$ | gamma's sensitivity to time | color |
| 3 | $\dfrac{\partial^3 V}{\partial S^2\,\partial \sigma}$ | gamma's sensitivity to volatility | zomma |

- The little "2" or "3" on the top counts the number of differentiations. On the bottom, $\partial S^2$ means "with respect to $S$, twice".
- **The order does not matter for mixed derivatives.** Asking "how does delta change with volatility?" gives the same number as "how does vega change with the underlying price?":

$$\frac{\partial}{\partial \sigma}\left(\frac{\partial V}{\partial S}\right) = \frac{\partial}{\partial S}\left(\frac{\partial V}{\partial \sigma}\right)$$

  That is why the book says vanna "can also refer to the sensitivity of the vega to a change in the underlying price. Both interpretations are mathematically identical." The same logic makes charm also "theta's sensitivity to the underlying price", color also "charm's sensitivity to the underlying price" and zomma also "vanna's sensitivity to the underlying price".

## Worked example
Check the vanna identity with numbers (our model, 110 call, 91 days, volatility 25%, underlying 100, no interest):
- Delta at volatility 24.5% and 25.5%: it rises by about **1.03 delta points** (whole-number delta) for one extra volatility point. So vanna $\approx 1.03$.
- Vega with the underlying at 99.5 and at 100.5: it rises by **0.0103** for one extra point of underlying.
- Same number, scaled by 100 only because delta is quoted in whole numbers ($1.03 \div 100 = 0.0103$). Both are vanna. ✓ ([[code/risk_measures_ii.ipynb]])

## Common confusions
- **You never differentiate by hand.** A pricing system gives all of these. What you need is the sentence: "this measure tells me how that other measure changes when this input changes."
- **"Higher order" does not mean "less important".** It means "a change of a change". Near expiration a third-order measure can matter more than a first-order one for a short-dated at-the-money position ([[concepts/09-risk-measurement-ii/short-dated-at-the-money-options-the-riskiest]]).
- **The names are not Greek letters.** Only some (gamma, theta, rho, lambda) are real Greek letters; vanna, charm, color, speed and zomma are trader nicknames.

## Related
- Maths needed first: [[00-maths-refresher/derivatives-and-rates-of-change]]
- Used in: [[chapters/09-risk-measurement-ii]]
