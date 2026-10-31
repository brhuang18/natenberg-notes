# Proportional, inversely proportional, and percentage change

**One-line summary:** "$A$ is proportional to $B$" means that doubling $B$ doubles $A$; "inversely proportional" means that doubling $B$ halves $A$. A **percentage change** compares a change with where you started, while a **point change** does not.

Used in: [[concepts/09-risk-measurement-ii/at-the-money-scaling-with-the-exercise-price]], [[concepts/09-risk-measurement-ii/lambda-leverage]], [[concepts/09-risk-measurement-ii/estimating-atm-theta-with-the-square-root-of-time]], [[chapters/09-risk-measurement-ii]]

## Intuition
- **Proportional:** apples at a fixed price per kilo. 3 kg costs 3 times as much as 1 kg. Cost and weight move together, and the ratio cost/weight never changes.
- **Inversely proportional:** a trip of fixed length. Drive twice as fast and the trip takes half as long. Speed and time move in opposite directions, and the product speed $\times$ time never changes.
- **Points vs percent:** a one-point move in a stock priced at 50 is a 2% move; the same one point in a stock priced at 100 is a 1% move. Option models think in percentages, so the same "one point" means different things at different price levels.

## The maths
**Proportional.** $A = k \times B$ for a fixed number $k$. The ratio $A/B = k$ stays the same.

**Inversely proportional.** $A = k / B$. The product $A \times B = k$ stays the same.

**Proportional to a square root.** $A = k \times \sqrt{B}$. To double $A$ you must *quadruple* $B$ (because $\sqrt{4} = 2$). This is the shape of "volatility over time" ([[concepts/06-volatility/scaling-volatility-for-time]]).

**Percentage change** from an old value to a new value:

$$\text{percentage change} = \frac{\text{new} - \text{old}}{\text{old}} \times 100\%$$

**Elasticity** (how many percent $A$ moves for each 1 percent that $B$ moves):

$$\text{elasticity} = \frac{\%\text{ change in } A}{\%\text{ change in } B} = \frac{\Delta A / A}{\Delta B / B} = \frac{\Delta A}{\Delta B} \times \frac{B}{A}$$

- Step 1 writes each percentage change as "change divided by starting level".
- Step 2 regroups: the first fraction $\Delta A/\Delta B$ is just a slope (for an option, the delta), and the second fraction $B/A$ is "starting level of $B$ over starting level of $A$". That is exactly the lambda formula $\Lambda = \Delta \times S/\text{TV}$.

## Worked example
**Proportional and inverse.** A call struck at 100 (underlying at 100) has a theta of $-0.0273$ and a gamma of 3.19. The same call struck at 50 (underlying at 50, all else equal) has:
- theta $-0.0137$: half of $-0.0273$, because theta is proportional to the exercise price (50 is half of 100);
- gamma $6.38$: double 3.19, because gamma is inversely proportional to the exercise price.

**Elasticity.** An option worth 4.00 has a delta of 0.20, the underlying is 100. A 1% rise in the underlying is $+1.00$; the option gains about $0.20 \times 1.00 = 0.20$, which is $0.20/4.00 = 5\%$. Elasticity $= 5\%/1\% = 5$. Check with the shortcut: $0.20 \times 100/4.00 = 5$. ✓

## Common confusions
- **Percent vs points of volatility.** Going from 20% to 21% volatility is a rise of **1 point** (vega is quoted per point) but a **5% relative** rise ($1/20$). Always check which the author means.
- **"Doubles" is not "adds the same".** If theta is proportional to the strike, strike 200 gives twice the theta of strike 100, not "100 more".
- **Inversely proportional is not negative.** Gamma at strike 200 is half of gamma at strike 100: smaller, but still positive.

## Related
- Maths needed first: [[00-maths-refresher/simple-interest-and-time-fractions]]
- See also: [[00-maths-refresher/standard-deviation-and-variance]] (why time scales with a square root)
