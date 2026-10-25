# Standard deviation and variance

**One-line summary:** the standard deviation is a typical distance of values from their average. Variance is its square. Variances of independent random steps add, which is why spread grows with the *square root* of time.

Used in: [[concepts/06-volatility/mean-and-standard-deviation]], [[concepts/06-volatility/scaling-volatility-for-time]], [[concepts/06-volatility/realized-volatility]], [[chapters/06-volatility]]

## Intuition
Two stocks both average 100. One finishes between 99 and 101 every time; the other swings between 60 and 140. The averages are equal, but the second is far more spread out. The standard deviation puts a number on "how spread out".

## The maths
For values $x_1, \dots, x_n$ with average (mean) $\bar x$:

| Step | What to do | Name |
|---|---|---|
| 1 | $\bar x = \dfrac{x_1 + \dots + x_n}{n}$ | the mean |
| 2 | for each value compute $x_i - \bar x$ | deviation from the mean |
| 3 | square each deviation: $(x_i - \bar x)^2$ | squares make everything positive |
| 4 | add the squares and divide by $n$ (or $n - 1$) | **variance** |
| 5 | take the square root | **standard deviation** |

$$\text{standard deviation} = \sqrt{\frac{\sum_{i=1}^{n}(x_i - \bar x)^2}{n}}$$

Why square the deviations? Deviations above and below the mean cancel to zero if you just add them; squaring makes them all positive. Taking the square root at the end puts the answer back into the original units.

**$n$ or $n - 1$?** If the numbers are the *whole* population, divide by $n$. If they are a *sample* used to estimate something bigger (as when you estimate volatility from some past days), dividing by $n - 1$ gives a better estimate. Volatility calculations usually use $n - 1$.

## Worked example 1 (small, to see the steps)
Values: 2, 4, 4, 4, 5, 5, 7, 9.

1. Mean: $(2 + 4 + 4 + 4 + 5 + 5 + 7 + 9)/8 = 40/8 = 5$.
2. Deviations: $-3, -1, -1, -1, 0, 0, 2, 4$.
3. Squares: $9, 1, 1, 1, 0, 0, 4, 16$; total $32$.
4. Variance (divide by 8): $32/8 = 4$.
5. Standard deviation: $\sqrt{4} = 2$.

## Worked example 2 (the book's five price changes)
Changes: $+0.98, -0.65, -0.70, +0.25, -0.85$.

1. Mean: $-0.99/5 = -0.198$.
2. Deviations: $1.178, -0.452, -0.502, 0.448, -0.652$.
3. Squares: $1.388, 0.204, 0.252, 0.201, 0.425$; total $2.470$.
4. Sample variance (divide by $n - 1 = 4$): $0.6175$.
5. Standard deviation: $\sqrt{0.6175} = 0.786$.

Annualize and express as a percent of the 45 price: $0.786 \times 16 / 45 = 27.9\%$. (Using log changes, as the book does, gives 27.8%.)

## Why time scales with a square root
Suppose each day's price change is random with standard deviation $s$, and days are independent. Then over $n$ days:
- **Variances add:** total variance $= n \times s^2$.
- So the standard deviation of the total is $\sqrt{n s^2} = s\sqrt{n}$.

Example: $s = 1$ per day. After 4 days the spread is $\sqrt{4} = 2$, not 4; after 16 days it is 4; after 256 days it is 16. That is exactly why annual volatility divided by $\sqrt{256} = 16$ gives the daily one.

(Note: it is the *variance* that adds, not the standard deviation. Adding standard deviations would overstate the spread because ups and downs partly cancel.)

## Common confusions
- **A big standard deviation does not mean a big average.** It is about spread, not level.
- **Standard deviation is in the same units as the data; variance is in squared units.** That is why traders quote the standard deviation.
- **Volatility is a standard deviation of *returns*** (percent changes), annualized, not of prices.

## Related
- Index: [[00-maths-refresher/README|Maths refresher]]
- Before: [[00-maths-refresher/probability-and-expected-value]] (the mean as an expected value), [[00-maths-refresher/summation-notation]]
