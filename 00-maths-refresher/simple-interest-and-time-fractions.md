# Simple interest and time as a fraction of a year

**One-line summary:** interest = amount × annual rate × time in years, and "time in years" is just months ÷ 12.

Used in: [[chapters/02-forward-pricing]], [[concepts/02-forward-pricing/forward-price-cost-and-benefit]]

## Intuition
A bank quotes interest as a yearly rate. If you borrow for only part of a year, you pay only that part of the yearly interest. Borrow for 6 months and you pay half a year's interest; borrow for 3 months and you pay a quarter.

## The maths

$$\text{interest} = P \times r \times t$$

- $P$ = the amount borrowed or lent (the "principal").
- $r$ = the interest rate **per year**, written as a decimal. 8% means $r = 0.08$ (divide the percent by 100).
- $t$ = the time **in years**. Turn months into years by dividing by 12: 3 months is $t = 3/12 = 0.25$, and 8 months is $t = 8/12 \approx 0.667$.

After the interest is added, you owe (or are owed) the original amount plus the interest:

$$\text{amount at the end} = P + P \times r \times t = P \times (1 + r \times t)$$

The step from the first form to the second is **factoring**: both terms contain $P$, so take it out the front. The bracket $(1 + r \times t)$ is called the **growth factor**. It says "one unit of money today becomes this many units at the end".

## Worked example
Borrow \$2,000 for 3 months at 8% a year (this is the property-tax loan in Chapter 2).

1. Convert the rate: $r = 8\% = 0.08$.
2. Convert the time: $t = 3/12 = 0.25$.
3. Interest: $2000 \times 0.08 \times 0.25 = 40$.
4. Total to repay: $2000 + 40 = 2040$.
5. Same answer through the growth factor: $2000 \times (1 + 0.08 \times 0.25) = 2000 \times 1.02 = 2040$.

## Going backwards: today's value of a future amount
If an amount is worth $A$ at the end, what is it worth today? Undo the growth by dividing:

$$P = \frac{A}{1 + r \times t}$$

Example: \$1,020 in 3 months at 8% is worth $1020 / 1.02 = \$1{,}000$ today.

## Common confusions
- **Forgetting that $r$ is per year.** If the loan lasts 8 months and you use $t = 8$ you will be wildly wrong. Use $8/12$.
- **Percent vs decimal.** Plug in 0.06, not 6.
- **Simple vs compound interest.** Here interest is added once at the end ("simple"). It is not re-invested part-way through. Natenberg uses this form for forward prices. Later chapters use *continuous compounding*, where the growth factor is $e^{rt}$ instead of $1 + rt$. For small $rt$ they are very close: with $r = 6\%$ and $t = 8/12$, $rt = 0.04$, and $1 + 0.04 = 1.04$ while $e^{0.04} \approx 1.0408$.

## Related
- Next: [[00-maths-refresher/rearranging-formulas]]
- Index: [[00-maths-refresher/README|Maths refresher]]
