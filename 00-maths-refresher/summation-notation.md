# Summation notation ($\sum$) and adding 1 + 2 + 3 + ...

**One-line summary:** $\sum$ is shorthand for "add up one term for each item in a list".

Used in: [[concepts/02-forward-pricing/forward-price-by-instrument]], [[concepts/02-forward-pricing/forward-price-cost-and-benefit]], [[chapters/02-forward-pricing]]

## Intuition
When a formula has to add up several similar pieces (say, one piece per dividend payment), writing "piece 1 + piece 2 + ... + piece n" gets long. The Greek capital letter sigma, $\sum$, means "add them all up".

## The maths
Chapter 2's forward price for a stock with dividends is

$$F = S(1 + rt) - \sum_{n} d_n \,(1 + r_n t_n)$$

Read the sum as: "for each dividend $n$, work out $d_n \times (1 + r_n t_n)$, then add all of those together."

- $d_n$ = the size of dividend number $n$.
- $t_n$ = time (in years) from that dividend's payment date to the maturity of the forward.
- $r_n$ = interest rate that applies over that period.
- $d_n(1 + r_n t_n)$ = that dividend plus the interest it earns between payment and maturity.

With two dividends the sum simply expands to $d_1(1 + r_1 t_1) + d_2(1 + r_2 t_2)$.

## Adding a run of whole numbers
In the land example Jerry gets \$500 at the end of each month. The \$500 from month $k$ earns interest for $12 - k$ months, so the interest months are $11, 10, 9, \dots, 1, 0$. Instead of adding them one by one, use

$$1 + 2 + 3 + \dots + n = \frac{n(n+1)}{2}$$

Why it works: write the list forwards and backwards and add them up column by column. Every column adds to $n + 1$, and there are $n$ columns, which counts everything twice, so divide by 2.

Example with $n = 11$: $1 + 2 + \dots + 11 = \dfrac{11 \times 12}{2} = 66$.

Interest on the oil revenue: each interest month earns $500 \times 0.08 / 12$ dollars, and there are 66 interest months in total:

$$\frac{500 \times 0.08}{12} \times 66 = 220$$

which matches the book's \$220.

## Common confusions
- $\sum$ is not a new operation, it is just repeated addition.
- In the book's formula the sum is written without limits ($\sum$ over "each dividend before maturity"). If there are no dividends, the sum is zero.

## Related
- Previous: [[00-maths-refresher/rearranging-formulas]]
- Index: [[00-maths-refresher/README|Maths refresher]]
