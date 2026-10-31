# Speed, color and zomma: how gamma changes

**One-line definition:** **speed** is how much gamma changes when the underlying moves one point, **color** (gamma decay) is how much gamma changes as a day passes, and **zomma** is how much gamma changes when volatility moves one point.

## Intuition
Gamma is the engine of an option position's *speed* risk, and these three tell you how steady the engine is.
- **Speed:** as the underlying moves toward the strike, gamma rises; away from it, gamma falls. Speed is that slope.
- **Color:** for an at-the-money option, gamma **grows as time passes** (the market is running out of time to hide in). Color measures how fast.
- **Zomma:** for an at-the-money option, gamma **falls when volatility rises**. Zomma measures how fast.

Where they are about zero, gamma is steady: "the gamma values of such options will be relatively insensitive".

## The maths
$$\text{speed} = \frac{\text{change in gamma}}{\text{1 point in the underlying}} \quad \text{color} = \frac{\text{change in gamma}}{\text{1 day passing}} \quad \text{zomma} = \frac{\text{change in gamma}}{\text{1 volatility point}}$$

![Speed, color and zomma against call delta](../../images/ch09-speed-color-zomma.png)

Reading the figure (calls; puts mirror):

| Option (91 days, volatility 25%) | Speed | Color (per day passing) | Zomma |
|---|---|---|---|
| Out of the money, delta about 5 | $+$ | $-$ (large) | $+$ (large) |
| Delta about 15 | $+$ (largest) | about 0 | about 0 |
| At the money | about 0 (slightly $-$) | $+$ (largest) | $-$ (largest) |
| Delta about 85 | $-$ (largest in size) | about 0 | about 0 |
| Delta about 95 | $-$ | $-$ (large) | $+$ (large) |

Key facts (all in the book's text):
- **Speed** is greatest for out-of-the-money options with deltas near 15 (puts: $-15$) and in-the-money options with deltas near 85 ($-85$). It is least for at-the-money options and for very deep in- or out-of-the-money options. Speed **declines** with more time or volatility and **rises** with less time or lower volatility.
- **Color** and **zomma** are largest for **at-the-money** options, with the **opposite sign** appearing near deltas 5 and 95. Both are about zero near deltas 15 and 85. Both grow when time or volatility fall (the gamma becomes "more sensitive"), and shrink when they rise.
- **Sign convention for color.** The book describes color from the point of view of *time to expiration*: "gamma values becoming smaller as we increase time to expiration and larger as we reduce time (**hence a negative color value**)" at the money. Our figure measures it per day **passing**, which is the opposite sign: at the money it is positive. Zomma has no such ambiguity.

## Worked example
At the money (underlying 100, strike 100, volatility 25%):

| | 91 days left | 30 days left |
|---|---|---|
| Gamma | 3.19 | 5.56 |
| Color (per day passing) | $+0.018$ | $+0.095$ |
| Zomma (per volatility point) | $-0.128$ | $-0.223$ |

- With 91 days left, one day later the gamma is about $3.19 + 0.018 = 3.21$ (the model says 3.207). With 30 days left it rises five times faster.
- If volatility rises one point from 25% to 26%, the 91-day gamma falls to about $3.19 - 0.128 = 3.06$ (the model says 3.067).

**Speed example.** A 15-delta call (strike about 114.7, 91 days, volatility 25%): gamma 1.87, speed $+0.136$. The underlying rises 1 point: gamma becomes about $1.87 + 0.14 = 2.00$ (model 2.00). An 85-delta call (strike about 88.55): gamma 1.87, speed $-0.174$; underlying up 1 point makes gamma $1.70$ (model 1.70) because the option moves further in the money.

## Common confusions
- **Gamma shape depends on where you are on the hump.** Speed is just "uphill or downhill on the gamma hump"; color and zomma are "how tall and narrow the hump is becoming".
- **Color has two signs in the literature.** If a source says "negative at the money", it measures against time *to* expiration.
- **Rarely used.** The book calls the whole group "nontraditional" and not every risk matters in every situation; the point is to know which conditions make them large.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/sensitivity-of-a-sensitivity]]
- Previous: [[concepts/09-risk-measurement-ii/gamma-in-different-conditions]]
- Next: [[concepts/09-risk-measurement-ii/short-dated-at-the-money-options-the-riskiest]]
- See also: [[concepts/09-risk-measurement-ii/summary-tables-where-each-measure-is-largest]], [[glossary]], [[formulas]]
