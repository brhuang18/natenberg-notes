# Present value and discounting

**One-line summary:** money you receive later is worth less than the same amount today, because today's money could be earning interest. *Discounting* brings a future amount back to today's value by dividing by a growth factor.

Used in: [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]], [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]], [[chapters/05-theoretical-pricing-models]]

## Intuition
Would you rather have 100 today or 100 in a year? Today, because you could put the 100 in the bank and have more than 100 in a year. So a promise of 100 in a year is worth *less than 100 today*. The question is how much less.

## The maths
This note uses simple interest, as in [[00-maths-refresher/simple-interest-and-time-fractions]]. If you invest $V$ today at rate $r$ per year for $t$ years, you end up with

$$\text{future amount } E = V\,(1 + r\,t)$$

Here $1 + rt$ is the **growth factor**. We usually know the future amount $E$ and want today's value $V$. Rearranging ([[00-maths-refresher/rearranging-formulas]]): divide both sides by $(1 + rt)$.

| Step | Result |
|---|---|
| Start | $E = V\,(1 + rt)$ |
| Divide both sides by $(1 + rt)$ | $\dfrac{E}{1 + rt} = V$ |

So:

$$\text{present value} = \frac{E}{1 + r\,t}$$

- $E$ = the amount you will receive (here, an expected value)
- $r$ = annual interest rate as a decimal (12% is $0.12$)
- $t$ = time in years (2 months is $2/12$)

Dividing by a number bigger than 1 makes the result smaller. A higher rate or a longer wait makes the growth factor bigger, so the present value is smaller.

## Worked example
The book's roulette bet pays an expected 0.95 in two months. Interest 12% a year.

1. $rt = 0.12 \times \dfrac{2}{12} = 0.02$.
2. Growth factor $= 1 + 0.02 = 1.02$.
3. Present value $= 0.95 / 1.02 = 0.9314 \approx 0.93$.

Check by going forward: 0.9314 grown by the growth factor is $0.9314 \times 1.02 = 0.95$. ✓.

Option version: an expected option payoff of 6.00 in two months is worth $6.00 / 1.02 = 5.88$ today.

## Common confusions
- **Divide, do not subtract.** The discount is not "take off 2%". Dividing by 1.02 takes off about 1.96%, because we undo growth.
- **Use the same time unit.** If $r$ is per year, $t$ must be in years.
- Real-world models often use *continuous compounding* ($e^{-rt}$, see the planned logarithms and exponentials topic); the book's examples here use simple interest, and for short times the numbers are very close.

## Related
- Index: [[00-maths-refresher/README|Maths refresher]]
