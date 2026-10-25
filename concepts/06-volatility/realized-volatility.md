# Realized volatility (historical and future)

**One-line definition:** realized volatility is the annualized standard deviation of the percent price changes of an underlying contract over some period. It is what the underlying actually did (historical) or will do (future).

## Intuition
Realized volatility is a measurement of the underlying: take a stretch of past prices, measure how jumpy the daily changes were, and express that as an annual percentage. To describe it you must say two things:
1. the **interval** between price observations (days, weeks, months),
2. the **number of intervals** used (50 of them, 250 of them...).

A "50-day volatility" uses 50 daily changes (about 10 weeks of trading days). A "52-week volatility" uses 52 weekly changes. On a chart, each point is the realized volatility over the *previous* 50 days (or 52 weeks), recomputed as time passes.

## The maths
**Step 1: price changes as percent (log) changes.** For prices $P_0, P_1, \dots, P_n$, the change from one period to the next is

$$u_i = \ln\!\left(\frac{P_i}{P_{i-1}}\right)$$

where $\ln$ is the natural logarithm. The book's footnote: volatility is most often calculated from *logarithmic* price changes, because continuous compounding turns returns into logs. For small moves, $\ln(P_i/P_{i-1})$ is almost exactly the percent change. See [[00-maths-refresher/exponentials-and-natural-logs]].

**Step 2: standard deviation of the changes.**

$$s = \sqrt{\frac{\sum_{i=1}^{n}(u_i - \bar u)^2}{n - 1}}$$

($\bar u$ is the average change.) See [[00-maths-refresher/standard-deviation-and-variance]].

**Step 3: annualize** ([[concepts/06-volatility/scaling-volatility-for-time]]). For daily data multiply by $\sqrt{256} = 16$:

$$\sigma_{\text{realized}} = s \times 16$$

## Worked example (the book's five days)
Stock at 45, daily changes $+0.98, -0.65, -0.70, +0.25, -0.85$.

1. Prices: 45.00, 45.98, 45.33, 44.63, 44.88, 44.03.
2. Log changes: $\ln(45.98/45) = +0.0215$, $\ln(45.33/45.98) = -0.0142$, and so on.
3. Standard deviation of those five numbers (using $n-1 = 4$): about $0.0174$.
4. Annualize: $0.0174 \times 16 = 0.278$, that is **27.8%**, matching the book.

(Using dollar changes instead gives $0.786 \times 16/45 = 27.9\%$, almost the same: for small moves logs and percents agree.)

## Historical vs future realized volatility
| | Meaning | Use |
|---|---|---|
| **Historical realized** | volatility over a past period | what we can measure |
| **Future realized** | volatility over the option's life | what we *need* |

The model needs the future realized volatility over the life of the option. If a trader knew it he would know the right odds, and like the casino ([[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]) he would profit in the long run even if he lost in the short run. Nobody knows it.

**Starting point: history.** If a contract's volatility has been between 10% and 30% over ten years, a guess of 5% or 40% makes little sense (not impossible, but unlikely without extraordinary circumstances). A guess in the 10-30% range is better, though still wide. A **volatility forecast model**, if you trust one, can narrow it further (the book defers these).

## Does the interval matter?
You can measure a one-year volatility from 250 daily changes, 52 weekly changes, or 12 monthly changes. For most underlyings the result is similar: a contract volatile from day to day is usually volatile week to week. The book's Figure 6-8 shows the S&P 500 250-day volatility from 2003 to 2012 calculated from daily, weekly and four-weekly changes. The curves are not identical but look alike, with no consistent bias.

## Common confusions
- **Realized volatility is a statistic of the past; the model needs one for the future.** They can differ a lot.
- **It is not "the volatility today".** It always uses a window of past data, and the choice of window changes the answer.
- **Business days only for daily data.** A 50-day volatility is about 10 weeks, not 50 calendar days.
- **Use the same interval when comparing.** A 250-day and a 52-week figure cover similar time but use different data.

## Related
- Chapter: [[chapters/06-volatility]]
- Maths needed: [[00-maths-refresher/standard-deviation-and-variance]], [[00-maths-refresher/exponentials-and-natural-logs]]
- Previous: [[concepts/06-volatility/lognormal-distributions]]
- Next: [[concepts/06-volatility/implied-volatility]]
- Earlier example: [[concepts/06-volatility/checking-volatility-against-price-changes]]
- Code: [[code/volatility.ipynb]]
- See also: [[glossary]], [[formulas]]
