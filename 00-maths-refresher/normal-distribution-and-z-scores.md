# The normal distribution and z-scores

**One-line summary:** the normal distribution is the symmetric bell curve described by a mean and a standard deviation. A *z-score* says how many standard deviations a value is from the mean, and from it you can read the probability.

Used in: [[concepts/06-volatility/random-walks-and-normal-distributions]], [[concepts/06-volatility/mean-and-standard-deviation]], [[concepts/06-volatility/volatility-as-a-standard-deviation]], [[chapters/06-volatility]]

## Intuition
Many random outcomes (heights, measurement errors, the sums of many small random steps) pile up in a bell shape: lots in the middle, fewer further out, symmetric on both sides. Once you know the centre and the typical spread, you know the whole shape.

## The maths
**The z-score** converts any value $x$ to "standard deviations from the mean":

$$z = \frac{x - \text{mean}}{\text{standard deviation}}$$

- $z = 0$: exactly at the mean.
- $z = +2$: two standard deviations above the mean.
- $z = -3.25$: three and a quarter standard deviations below.

**Probability inside a range** (the 68-95-99.7 rule):

| Within $\pm z$ standard deviations | Probability inside | Probability outside (both tails) |
|---|---|---|
| 1 | 68.3% | 31.7% |
| 2 | 95.4% | 4.6% |
| 3 | 99.7% | 0.3% |

Each tail gets half of the "outside" amount, because the curve is symmetric.

**Other values.** Use a table, a spreadsheet function (`NORM.S.DIST(z, TRUE)` in Excel gives the chance of being *below* $z$) or, in Python, `0.5 * (1 + math.erf(z / math.sqrt(2)))`. The notebook defines this as `N(z)`.

| $z$ | Chance of being below $z$ |
|---|---|
| $-3$ | 0.13% |
| $-2$ | 2.3% |
| $-1$ | 15.9% |
| $0$ | 50% |
| $+1$ | 84.1% |
| $+2$ | 97.7% |

## Worked example
The book's contract: mean (forward) 100, volatility 20%, so the standard deviation is 20. Price one year later: 35.

1. Distance from the mean: $35 - 100 = -65$.
2. $z = -65/20 = -3.25$.
3. Chance of being at or below 35: $N(-3.25) \approx 0.00058$, which is $0.058\%$, about 1 in 1,700.
4. Compare the 68-95-99.7 rule: beyond $z = 3$ is only 0.3% on both sides together, so $z = -3.25$ is rarer than that.

Another: troughs in the pinball maze, mean 7.5, standard deviation 3. Trough number 14 is $14 - 7.5 = 6.5$ above the mean, $z = 6.5/3 \approx 2.2$. Beyond two standard deviations, so rare (at most about 2.3% for troughs from 14 up).

## Common confusions
- **Percent vs standard deviations.** "20% volatility" is one standard deviation; the 2-standard-deviation range is $\pm 40\%$.
- **Both tails vs one tail.** The 4.6% outside two standard deviations is split 2.3% / 2.3%.
- **A normal distribution allows negative values**, so for prices the lognormal is used ([[concepts/06-volatility/lognormal-distributions]]).

## Related
- Index: [[00-maths-refresher/README|Maths refresher]]
- Before: [[00-maths-refresher/standard-deviation-and-variance]], [[00-maths-refresher/probability-and-expected-value]]
