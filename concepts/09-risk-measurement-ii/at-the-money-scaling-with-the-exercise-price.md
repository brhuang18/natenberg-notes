# At-the-money options: how theta, vega and gamma scale with the exercise price

**One-line definition:** for at-the-money options that are otherwise identical, value, theta and vega are **proportional** to the exercise price, while gamma is **inversely proportional** to it.

## Intuition
Imagine two identical at-the-money options except that every price in the second is ten times bigger (strike 1,000 instead of 100; underlying 1,000 instead of 100). The second option is like holding **ten copies** of the first. So:
- **Value, theta and vega** (all measured in price units) are ten times larger.
- **Delta** is unchanged: a 1% move in the underlying has the same *percentage* effect, so the same share of the underlying is "owned" by the option.
- **Gamma** is delta change per **one point** of underlying. One point on a 1,000 underlying is a tiny 0.1% move, one point on a 100 underlying is a 1% move. A smaller percentage move changes delta less, so gamma is ten times smaller.

The book's version: a one-point move at 50 is a 2% change, bigger than a one-point move at 100 (1%), and "theoretical pricing models measure change in percentage terms".

## The maths
Let $K$ be the exercise price (and underlying price) of an at-the-money option, other inputs the same.

$$\text{value} \propto K \qquad \Theta \propto K \qquad \text{vega} \propto K \qquad \Gamma \propto \frac{1}{K}$$

Comparing two at-the-money options with strikes $K_1$ and $K_2$:

$$\frac{\Theta_2}{\Theta_1} = \frac{\text{vega}_2}{\text{vega}_1} = \frac{K_2}{K_1} \qquad \frac{\Gamma_2}{\Gamma_1} = \frac{K_1}{K_2}$$

![At-the-money ratios against the exercise price](../../images/ch09-gamma-profiles.png)

(The right-hand panel shows vega and theta rising along a straight line through the origin and gamma falling along a curve, all relative to the 100 option.)

## Worked example
At the money, 91 days, volatility 25%, no interest (our model, [[code/risk_measures_ii.ipynb]]):

| Strike | Value | Theta | Vega | Gamma |
|---|---|---|---|---|
| 50 | 2.488 | $-0.0137$ | 0.0994 | 6.379 |
| 100 | 4.977 | $-0.0273$ | 0.1988 | 3.190 |
| 1,000 | 49.767 | $-0.2731$ | 1.9881 | 0.319 |

Check the book's statements:
- The 100 option has twice the vega of the 50 option: $0.1988/0.0994 = 2.0$. ✓
- The 1,000 option is worth 10 times the 100 option (and its theta is 10 times): $49.767/4.977 = 10.0$. ✓
- The 50 option has twice the gamma of the 100 option: $6.379/3.190 = 2.0$. ✓

**What this means in practice.** A trader comparing an at-the-money option on a 50 stock with one on a 500 stock cannot compare their gamma or vega numbers directly. Adjust for the price level first, or think in percentages (this is one reason traders also quote [[concepts/09-risk-measurement-ii/lambda-leverage]]).

## Common confusions
- **Only for at-the-money.** For the same stock, different strikes do not scale like this.
- **Not "bigger underlying means bigger gamma".** It is the opposite for gamma.
- **It is the percentage view that matters.** All three results come from one fact: models work in percentages.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/proportionality-and-percentage-change]]
- Previous: [[concepts/09-risk-measurement-ii/estimating-atm-theta-with-the-square-root-of-time]]
- Next: [[concepts/09-risk-measurement-ii/vega-in-different-conditions]]
- See also: [[concepts/09-risk-measurement-ii/theta-in-different-conditions]], [[concepts/09-risk-measurement-ii/gamma-in-different-conditions]], [[glossary]], [[formulas]]
