# The five P&L components and discounting (Figure 8-2)

**One-line definition:** the final profit of a dynamic hedge is the sum of five pieces (original hedge, adjustments, and three interest items); discounting that sum back to today gives a number we can compare with the model's predicted profit.

## Intuition
A hedge touches cash in several ways. We pay for options, receive cash when we short stock, pay or receive cash each time we adjust, and every one of those cash amounts either earns interest or costs interest until expiration. Add up everything at expiration and you have a total in *future* money. To compare with the model's prediction (which is a value *today*) you divide by a growth factor.

## The components
| # | Component | What it is | In the example |
|---|---|---|---|
| 1 | Original hedge | option P&L plus stock P&L, closed at expiration | $-422.50$ |
| 2 | Adjustments | all the weekly trades in the underlying plus the final buy-back | $+467.55$ |
| 3 | Carry on the options | interest *lost* on the money paid for the calls | $-5.75$ |
| 4 | Interest on the stock position | interest *earned* on the proceeds of the original short | $+56.21$ |
| 5 | Interest on the adjustments | interest earned or paid on each week's cash flow | $-5.27$ |

**Component 3.** We paid $100 \times 5.00 = 500.00$ at the start. That money could have been earning 6% for 70 days:

$$-500.00 \times 6\% \times \frac{70}{365} = -5.75$$

**Component 4.** We sold 50 contracts at 97.70, a credit of $50 \times 97.70 = 4{,}885.00$ that earns interest for the full 70 days:

$$+4{,}885.00 \times 6\% \times \frac{70}{365} = +56.21$$

**Component 5.** Each week's trade is a credit (sell) or a debit (buy) for the weeks that remain. Week 1: $+398.00 \times 6\% \times 63/365 = +4.12$. Week 2: $-1{,}762.25 \times 6\% \times 56/365 = -16.22$. Add all nine weeks: $-5.27$. (The book's text says $-5.28$, but Figure 8-2 and the column both give $-5.27$.)

## Adding up and discounting
$$-422.50 + 467.55 - 5.75 + 56.21 - 5.27 = 90.24$$

This is cash at expiration, 70 days from now. Present value, dividing by the growth factor $1 + rt$ ([[00-maths-refresher/present-value-and-discounting]]):

$$\frac{90.24}{1 + 0.06 \times \frac{70}{365}} = \frac{90.24}{1.011507} = 89.21$$

The model's prediction was $100 \times (5.89 - 5.00) = 89.00$. The two agree to 0.21.

![Profit and loss components](../../images/ch08-pnl-components.png)

## Dividends
The example has no dividend. If there were one, any long stock position (from the original hedge or the adjustments) would *receive* it, and any short stock position would *pay* it, plus interest on that dividend from its payment date to expiration. The dividend and its interest then become another part of the profit or loss.

## Why the sum comes out near the prediction
It is not a coincidence in the model's world: the model values the option as the cost of replicating it with the hedge ([[concepts/08-dynamic-hedging/option-replication-and-the-hedging-principle]]). We bought the real call for 5.00; the hedge, in effect, *sells it back* at its theoretical 5.89. The profit is the difference, 0.89 per option, 89 in total. In the real world a single path will not hit it exactly: the book admits the example was "carefully constructed", and our simulation shows typical scatter of tens around 89. [[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]]

## Common confusions
- **Do not mix up "profit on the option" and "profit on the hedge".** The option alone lost money here (3.85 vs 5.00). Only the whole package matters.
- **Which interest rate?** We assume one constant rate for lending and borrowing (a frictionless market). In reality the borrowing rate is higher than the lending rate and the short-stock rebate is lower than the lending rate. The book says interest is usually the *least important* input. [[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]]
- **Why discount?** The 90.24 is money at expiration; the 89.00 prediction is money today. Dividing by $1 + 0.06 \times 70/365$ puts both on the same footing.
- **Rounding.** Our unrounded total is 90.23; the book's 90.24 comes from adding the rounded components.

## Related
- Chapter: [[chapters/08-dynamic-hedging]]
- Previous: [[concepts/08-dynamic-hedging/stock-option-hedge-walkthrough]]
- Next: [[concepts/08-dynamic-hedging/gamma-and-the-unhedged-amount]]
- Maths needed: [[00-maths-refresher/simple-interest-and-time-fractions]], [[00-maths-refresher/present-value-and-discounting]], [[00-maths-refresher/summation-notation]]
- See also: [[glossary]], [[formulas]]
