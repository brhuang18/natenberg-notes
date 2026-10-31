# Estimating the theta of an at-the-money option (the square-root-of-time rule)

**One-line definition:** because an at-the-money option's value is proportional to the square root of the time left, one day later its value is $\sqrt{(t-1)/t}$ times today's, and its theta is the difference.

## Intuition
We have two facts about an at-the-money option:
1. Its value is proportional to volatility (theta, which measures value-melting, is proportional to volatility, [[concepts/09-risk-measurement-ii/theta-in-different-conditions]]).
2. Volatility over a period is proportional to the **square root of time** ([[concepts/06-volatility/scaling-volatility-for-time]]).

Put them together: the value of an at-the-money option is proportional to $\sqrt{\text{days left}}$. Then "tomorrow's value" is easy to predict from "today's value" and the decay is the gap between them.

The book says plainly that this works **only for at-the-money options**: "There is no convenient method for estimating the theta of in-the-money and out-of-the-money options."

## The maths
Let $TV_t$ be the theoretical value with $t$ days to expiration.

**Step 1.** Value proportional to $\sqrt{t}$ means the ratio of two values equals the ratio of the square roots of their times:

$$\frac{TV_{t-1}}{TV_t} = \frac{\sqrt{t-1}}{\sqrt{t}} = \sqrt{\frac{t-1}{t}}$$

**Step 2.** Multiply both sides by $TV_t$:

$$TV_{t-1} = TV_t \times \sqrt{\frac{t-1}{t}}$$

**Step 3.** Theta is the value lost in one day, today's value minus tomorrow's:

$$\Theta = TV_t - TV_{t-1} = TV_t \times \left(1 - \sqrt{\frac{t-1}{t}}\right)$$

**Why theta keeps growing.** The bracket $1 - \sqrt{(t-1)/t}$ gets larger as $t$ gets smaller. Try it:

| Days left $t$ | $\sqrt{(t-1)/t}$ | Bracket $1 - \sqrt{(t-1)/t}$ |
|---|---|---|
| 30 | 0.98319 | 0.01681 |
| 10 | 0.94868 | 0.05132 |
| 2 | 0.70711 | 0.29289 |

**A shortcut (ours, not the book's).** For large $t$, $\sqrt{1 - x} \approx 1 - x/2$ when $x$ is small. With $x = 1/t$ the bracket becomes about $1/(2t)$, so

$$\Theta \approx \frac{TV_t}{2t}$$

(today's value divided by twice the number of days left). With 30 days: $2.50/(2 \times 30) = 0.0417$, against the exact 0.0420.

## Worked example (the book's)
An at-the-money option worth 2.50 with 30 days left.

1. Today: $\Theta = 2.50 \times \left(1 - \sqrt{29/30}\right) = 2.50 \times (1 - 0.98319) = 2.50 \times 0.01681 \approx 0.042$.
2. Tomorrow the value is $2.50 - 0.042 = 2.458$ with 29 days left.
3. Tomorrow's theta: $2.458 \times \left(1 - \sqrt{28/29}\right) = 2.458 \times (1 - 0.98263) = 2.458 \times 0.01737 \approx 0.0427$. The book rounds to 0.043.

Theta rose from 0.042 to 0.043 in one day, with the time still a month away. ([[code/risk_measures_ii.ipynb]] checks both steps against a model: for a 30-day at-the-money option worth 2.50 at volatility 21.9%, the model's true one-day decays are 0.0420 and 0.0427.)

## Common confusions
- **This is the decay over a whole day**, from $t$ days to $t-1$ days, not the instantaneous slope the pricing model reports. They differ slightly (the model's theta at 30 days is $-0.0417$, the one-day decay is $-0.0420$) because theta is itself rising.
- **At the money only, and when the strike equals the forward price.** With interest, dividends or a skew the "at the money" option is not exactly proportional to $\sqrt{t}$.
- **The book cites Figure 9-7** after this passage; it means Figure 9-10 (theta over time). Figure 9-7 is the charm.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/proportionality-and-percentage-change]], [[00-maths-refresher/standard-deviation-and-variance]]
- Previous: [[concepts/09-risk-measurement-ii/theta-in-different-conditions]]
- Next: [[concepts/09-risk-measurement-ii/at-the-money-scaling-with-the-exercise-price]]
- See also: [[concepts/07-risk-measurement-i/theta]], [[glossary]], [[formulas]]
