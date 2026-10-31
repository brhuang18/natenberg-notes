# Higher-order sensitivities and their names

**One-line definition:** the risk measures are not fixed numbers; each one changes when the underlying price, volatility or time changes, and the traders' names for those changes (gamma, vanna, charm, volga, vega decay, speed, color, zomma) are all the same idea: **the sensitivity of a sensitivity**.

## Intuition
Chapter 7 gave you five numbers (delta, gamma, theta, vega, rho) and a way to add them up for a whole position. Chapter 9 says: those numbers describe the position **today, in today's market**. Move the underlying, change volatility, or just let a day pass, and every one of them shifts. "Today's small risk can become tomorrow's big risk."

Take a position that is delta neutral right now. There are three different reasons its delta can stop being zero tomorrow, even though you did nothing:

| What happened | Which sensitivity says how much delta moves |
|---|---|
| The underlying moved | gamma (Chapter 7) |
| Volatility changed | vanna |
| A day went by | charm |

The same three questions can be asked of vega and of gamma. That gives a small grid, and the names are just labels for its boxes.

## The grid of names

| The measure that changes $\downarrow$ | when the underlying price moves | when volatility moves | when time passes |
|---|---|---|---|
| **Delta** | gamma | **vanna** | **charm** (delta decay) |
| **Vega** | vanna (the same number) | **volga** (vomma) | **vega decay** |
| **Gamma** | **speed** | **zomma** | **color** (gamma decay) |

- **Second order** (a sensitivity of a first-order measure): gamma, vanna, charm, volga, vega decay. **Third order** (a sensitivity of gamma): speed, color, zomma.
- Vanna appears twice because "how delta changes with volatility" and "how vega changes with the underlying price" are mathematically the same number ([[00-maths-refresher/sensitivity-of-a-sensitivity]]).
- The book does not name any sensitivity of theta; it simply describes how theta behaves (Figures 9-8 to 9-11, [[concepts/09-risk-measurement-ii/theta-in-different-conditions]]).
- **Lambda** is not in the grid. It is delta re-expressed in percentages ([[concepts/09-risk-measurement-ii/lambda-leverage]]).

## The maths
For a small change, each new value is the old value plus (size of change) $\times$ (sensitivity). Updating the delta for a move of $\Delta S$ in the underlying, $\Delta\sigma$ volatility points and $d$ days:

$$\Delta_{\text{new}} \approx \Delta + \Delta S \times \Gamma + \Delta\sigma \times \text{vanna} + d \times \text{charm}$$

Likewise

$$\text{vega}_{\text{new}} \approx \text{vega} + \Delta S \times \frac{\text{vanna}}{100} + \Delta\sigma \times \text{volga} + d \times \text{vega decay}$$

$$\Gamma_{\text{new}} \approx \Gamma + \Delta S \times \text{speed} + \Delta\sigma \times \text{zomma} + d \times \text{color}$$

- Symbols: $\Delta S$ in points; $\Delta\sigma$ in volatility points; $d$ days that pass; delta and gamma in whole numbers (delta 24 means 0.24). The $/100$ on vanna in the vega line is only a units conversion because delta is in whole numbers.
- These are "first-order" updates: they ignore the fact that each sensitivity itself keeps changing. They are our own link, not printed in the book; good for small moves only.

## Worked example
A 110 call, underlying 100, 91 days to expiration, volatility 25% (no interest, from [[code/risk_measures_ii.ipynb]]). Today: delta 24.16, gamma 2.50, vanna 1.03, charm $-0.14$ per day.

Tomorrow the underlying has risen 1 point, volatility has risen 2 points, and one day has passed:

| Step | Calculation | Change in delta |
|---|---|---|
| Underlying $+1$ | $1 \times 2.50$ | $+2.50$ |
| Volatility $+2$ | $2 \times 1.03$ | $+2.06$ |
| One day | $1 \times (-0.14)$ | $-0.14$ |
| **New delta (estimate)** | $24.16 + 2.50 + 2.06 - 0.14$ | **28.58** |

Recomputing the model with all three changes at once gives 28.45. So the estimate is close, and **gamma and vanna moved the delta by similar amounts**: the volatility move mattered about as much as the price move.

## Common confusions
- **Nothing here is a new risk.** It is the same value surface looked at from different angles. If you understand "slope of a slope", you understand every name in the table.
- **Which sign is "decay"?** Charm, vega decay and color are quoted here as the change *per day that passes*. The book's formulas differentiate with respect to time **to** expiration, which flips the sign (it says outright that ATM color is "negative", which is the change per extra day of life). Check the sign convention whenever you meet one of these numbers.
- **Not every measure matters in every trade.** The book says so: "it is impractical to analyze every potential risk"; the aim is to know *which* conditions make each measure large.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/sensitivity-of-a-sensitivity]], [[00-maths-refresher/derivatives-and-rates-of-change]]
- Built on: [[concepts/07-risk-measurement-i/delta]], [[concepts/07-risk-measurement-i/gamma]], [[concepts/07-risk-measurement-i/vega]]
- Next: [[concepts/09-risk-measurement-ii/time-and-volatility-have-similar-effects]]
- See also: [[concepts/09-risk-measurement-ii/summary-tables-where-each-measure-is-largest]], [[glossary]], [[formulas]]
