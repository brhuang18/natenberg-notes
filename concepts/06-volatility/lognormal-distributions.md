# Lognormal distributions

**One-line definition:** a lognormal distribution is what you get when *percent* price changes are normally distributed and compound continuously: prices can never fall below zero, and the distribution is skewed to the upside.

## Intuition
A normal distribution has a flaw for prices: it is symmetrical. If a 50 contract can rise by 75 to 125, a normal model must allow it to fall by 75 to **-25**. Stocks and commodities cannot have negative prices.

The fix is to think in **percent returns**. Returns compound: a 12% gain applied to a bigger and bigger base. A loss of 100% takes you to exactly zero but no lower. So a lognormal price has a hard floor at 0 and a long tail to the upside.

## Compounding frequency (the book's tables)
Invest 1,000 for one year at a stated 12% a year, paid at different frequencies:

| Payments | Amount after one year | Total yield |
|---|---|---|
| 12% once a year | 1,120.00 | 12.00% |
| 6% twice a year | 1,123.60 | 12.36% |
| 3% every three months | 1,125.51 | 12.55% |
| 1% every month | 1,126.83 | 12.68% |
| 12%/52 every week | 1,127.34 | 12.73% |
| 12%/365 every day | 1,127.47 | 12.75% |
| 12% compounded continuously | 1,127.50 | 12.75% |

The more often interest is paid, the more you earn, up to a limit: **continuous compounding**, as if interest were paid at every instant.

Now a *negative* rate, a loss of 12% a year:

| Payments | Amount after one year | Total yield |
|---|---|---|
| $-12\%$ once a year | 880.00 | $-12.00\%$ |
| $-6\%$ twice a year | 883.60 | $-11.64\%$ |
| $-1\%$ every month | 886.38 | $-11.36\%$ |
| $-12\%/365$ every day | 886.90 | $-11.31\%$ |
| $-12\%$ continuously | 886.92 | $-11.31\%$ |

More frequent compounding means a *smaller* loss.

## The maths
Continuous compounding uses the exponential function:

$$1000 \times e^{0.12} = 1127.50 \qquad\qquad 1000 \times e^{-0.12} = 886.92$$

- $e \approx 2.71828$ and $e^{x}$ (also written $\exp(x)$) is the result of compounding continuously at rate $x$ for one year. See [[00-maths-refresher/exponentials-and-natural-logs]].

**Up and down are not mirror images.**
- Gain after one year at $+12\%$ continuous: $1127.50 - 1000 = +127.50$.
- Loss at $-12\%$ continuous: $1000 - 886.92 = -113.08$.

The *rate* is the same 12% in both directions, but the dollar gain is bigger than the loss. If 12% is a volatility, a one-standard-deviation move **up** is $+127.50$ and **down** is $-113.08$. That is the skew.

**Floor at zero.** However negative the rate, $e^{-x}$ stays positive, so the value never reaches zero or goes below it.

## The mean sits to the right of the peak
In a normal distribution the peak (the *mode*) and the mean are in the same spot. In a lognormal distribution the right tail is long and the left tail is cut off at zero, so there is more "weight" to the right. The mean, the balance point, must be to the right of the peak.

![Normal vs lognormal](../../images/ch06-normal-vs-lognormal.png)

The picture uses our own numbers (forward 100, six months, volatility 30%): the mean is 100 in both, but the lognormal peak is near 93.

## Effect on option values
The book's example: forward 100, six months, volatility 30%, a 90 put and a 110 call (each 10% out of the money).

| | Normal (book) | Lognormal (book) | Our recomputation |
|---|---|---|---|
| 90 put | 4.37 | 4.00 | normal 4.39, lognormal 3.99 |
| 110 call | 4.37 | 4.74 | normal 4.39, lognormal 4.75 |

(Small differences are because the book does not spell out every convention; the pattern is identical.)

- **Normal:** call and put are equally far out of the money, so they have the same value.
- **Lognormal (Black-Scholes):** the 110 call is worth more. Its value can grow without limit, while the 90 put can never be worth more than 90, since the price cannot go below zero.

Real markets do not have to agree: a 90 put can trade above a 110 call. One possible reason is that the market does not fully believe a lognormal distribution describes prices. "And perhaps the marketplace is right!"

## Black-Scholes is a continuous-time model
It assumes volatility compounds continuously, as if price changes (up or down) happen constantly at an annual rate corresponding to the volatility. This is why the model's price distribution at expiration is lognormal.

## Common confusions
- **Lognormal does not mean the percent moves are skewed.** The *percent* changes are normal; the *prices* that result are skewed.
- **The volatility number is still a percent.** The lognormal shape is a refinement, not a different volatility.
- **Why not just use normal for short periods?** Over days or weeks the two are almost identical; the difference shows over longer periods and far-from-the-money strikes.

## Related
- Chapter: [[chapters/06-volatility]]
- Maths needed: [[00-maths-refresher/exponentials-and-natural-logs]], [[00-maths-refresher/normal-distribution-and-z-scores]]
- Previous: [[concepts/06-volatility/interest-rate-products-and-rate-volatility]]
- Next: [[concepts/06-volatility/realized-volatility]]
- Earlier: [[concepts/02-forward-pricing/forward-price-by-instrument]] (simple interest used there; this note introduces continuous compounding)
- Code: [[code/volatility.ipynb]]
- See also: [[glossary]], [[formulas]]
