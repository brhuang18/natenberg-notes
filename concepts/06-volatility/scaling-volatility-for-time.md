# Scaling volatility for time (the square-root rule)

**One-line definition:** volatility is always quoted per year. To get the standard deviation over a shorter or longer period, multiply the annual volatility by the **square root of the time in years**.

## Intuition
Interest is proportional to time: 6% a year is 3% in six months. Volatility is not. Randomness behaves differently: random ups and downs partly cancel each other out. Walk a hundred steps in random directions and you end up about 10 steps from where you started (not 100). Quadruple the time and the typical distance only *doubles*.

So the typical price move grows like $\sqrt{\text{time}}$:

| Time | Typical move relative to one year |
|---|---|
| 1 year | $1\times$ |
| 3 months ($\tfrac{1}{4}$ year) | $\sqrt{1/4} = \tfrac{1}{2}\times$ |
| 1 day ($\tfrac{1}{256}$ year) | $\sqrt{1/256} = \tfrac{1}{16}\times$ |

## The maths

$$\sigma_t = \sigma_{\text{annual}} \times \sqrt{t}, \qquad t \text{ in years}$$

- Why a square root: when independent random steps are added, their **variances** (standard deviation squared) add. For $n$ steps each with standard deviation $s$, the variance is $n s^2$, so the standard deviation of the total is $s\sqrt{n}$. See [[00-maths-refresher/standard-deviation-and-variance]].

**Shortcuts traders use.** Only trading days count when observing prices (weekends and holidays have no price changes). Exchanges have roughly 250 to 260 trading days; traders assume **256** because $\sqrt{256} = 16$ exactly.

$$\sigma_{\text{daily}} = \frac{\sigma_{\text{annual}}}{\sqrt{256}} = \frac{\sigma_{\text{annual}}}{16}$$

For weekly changes use all 52 weeks:

$$\sigma_{\text{weekly}} = \frac{\sigma_{\text{annual}}}{\sqrt{52}} \approx \frac{\sigma_{\text{annual}}}{7.2}$$

A one-standard-deviation move in price units is the price times that percentage. For short periods the forward is so close to the current price that traders centre the distribution on the current price.

## Worked example 1: contract at 100, volatility 20%
- Daily: $20\%/16 = 1.25\%$, so one standard deviation $= 1.25$. Two: $2.50$.
  - A move of 1.25 or less on about 2 trading days out of 3.
  - A move of 2.50 or less on about 19 days out of 20; more than 2.50 only about 1 day in 20.
- Weekly: $20\%/7.2 = 2.78\%$, so one standard deviation $\approx 2.78$ (exactly 2.77 using $\sqrt{52} = 7.211$). Two: $\approx 5.56$.

## Worked example 2: stock at 45, volatility 37%
| Period | Divide by | One st. dev. | Range, 1 st. dev. | Range, 2 st. dev. |
|---|---|---|---|---|
| Day | 16 | $45 \times 0.37/16 = 1.04$ | 43.96 to 46.04 | 42.92 to 47.08 |
| Week | 7.2 | $45 \times 0.37/7.2 = 2.31$ | 42.69 to 47.31 | 40.38 to 49.62 |

Step by step for the daily number: $0.37 / 16 = 0.023125$; $45 \times 0.023125 = 1.04$.

## Going the other way
From a daily standard deviation back to annual: multiply by 16. A stock that typically moves 1% a day (one standard deviation) has a volatility of about $1\% \times 16 = 16\%$. This is how traders turn observed price changes into a volatility ([[concepts/06-volatility/realized-volatility]]).

## Two practical benchmarks
- Because $1 - 0.954 \approx 1/20$ and a month has about 20 trading days, expect a **daily two-standard-deviation move about once a month**.
- Two thirds of days should be inside one standard deviation.

## Common confusions
- **Never scale volatility linearly.** Dividing annual volatility by 256 gives a daily number that is 16 times too small.
- **Annual volatility is not a yearly move limit.** It is a one-standard-deviation range; a third of years will be outside it.
- **Why 256 and not 365 or 252?** The convenient square root. Alternatives are fine; the difference is small. The book also notes electronic markets may justify using 365 days for some contracts.
- Time inside an option model is a different calculation (calendar days / 365; the model handles trading days). See [[concepts/05-theoretical-pricing-models/choosing-the-inputs]].

## Related
- Chapter: [[chapters/06-volatility]]
- Maths needed: [[00-maths-refresher/standard-deviation-and-variance]]
- Previous: [[concepts/06-volatility/volatility-as-a-standard-deviation]]
- Next: [[concepts/06-volatility/checking-volatility-against-price-changes]]
- Code: [[code/volatility.ipynb]]
- See also: [[glossary]], [[formulas]]
