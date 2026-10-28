# The stock-option hedge, step by step (Figure 8-1)

**One-line definition:** a complete 10-week example of buying an underpriced call, hedging it delta neutral, adjusting each week, and closing out at expiration.

## Intuition
We follow every dollar. At the start we have a hunch worth +89 (the call is worth 5.89 and costs 5.00, 100 times). The stock then wanders, and at the end it is at 103.85. If we had simply bought the calls and shorted the stock once and then walked away, we would be down 422.50. The weekly adjustments are what turn that into a profit.

## The setup
| Item | Value |
|---|---|
| Stock price | 97.70 |
| Time to June expiration | 10 weeks (70 days) |
| Interest rate | 6.00% |
| Volatility we believe (crystal ball) | 37.62% |
| June 100 call | price 5.00 (implied volatility 32.40%), theoretical value 5.89, delta 50 |
| Position | buy 100 calls, sell 50 underlying contracts |

(Recomputed: our model gives 5.89 and delta 50.4, and the implied volatility of 5.00 is 32.40%.)

## Week by week (Figure 8-1)
Each row is the state *at the end of that week*. "Short in total" counts the original 50 short plus all adjustments. The cash is price times contracts, positive when selling. Interest is on that cash for the days remaining to expiration, at 6%.

| Week | Price | Call delta | Total delta before trade | Trade | Short in total | Cash flow | Interest |
|---|---|---|---|---|---|---|---|
| 0 | 97.70 | 50 | 0 | start | 50 | | |
| 1 | 99.50 | 54 | $+400$ | sell 4 | 54 | $+398.00$ | $+4.12$ |
| 2 | 92.75 | 35 | $-1{,}900$ | buy 19 | 35 | $-1{,}762.25$ | $-16.22$ |
| 3 | 95.85 | 43 | $+800$ | sell 8 | 43 | $+766.80$ | $+6.18$ |
| 4 | 96.20 | 43 | 0 | none | 43 | 0 | 0 |
| 5 | 102.45 | 62 | $+1{,}900$ | sell 19 | 62 | $+1{,}946.55$ | $+11.20$ |
| 6 | 93.30 | 28 | $-3{,}400$ | buy 34 | 28 | $-3{,}172.20$ | $-14.60$ |
| 7 | 91.15 | 17 | $-1{,}100$ | buy 11 | 17 | $-1{,}002.65$ | $-3.46$ |
| 8 | 95.20 | 27 | $+1{,}000$ | sell 10 | 27 | $+952.00$ | $+2.19$ |
| 9 | 102.80 | 72 | $+4{,}500$ | sell 45 | 72 | $+4{,}626.00$ | $+5.32$ |
| 10 | 103.85 | | | close out | | see below | |

(Interest for week 1 uses 63 days left: $398.00 \times 6\% \times 63/365 = 4.12$. Week 2 uses 56 days, and so on, one week fewer each time.)

## Closing out at expiration (week 10, underlying 103.85)
The calls are 3.85 in the money. We sell them at parity (or exercise and offset) and buy back every underlying contract still short.

**Original hedge**

$$\text{options: } 100 \times (3.85 - 5.00) = -115.00$$

$$\text{stock: } 50 \times (97.70 - 103.85) = -307.50$$

$$\text{total: } -422.50$$

The stock rose from 97.70 to 103.85, so the 50 shorts lost 307.50, and the option gained only 3.85 against a cost of 5.00. "This certainly does not appear to have been successful."

**Adjustments.** After week 9 we were short 72 in total, of which 50 belong to the original hedge, so the adjustments leave us short 22. At expiration we buy these back at 103.85: $-22 \times 103.85 = -2{,}284.70$. Adding every weekly cash flow and this last one:

$$398.00 - 1{,}762.25 + 766.80 + 0 + 1{,}946.55 - 3{,}172.20 - 1{,}002.65 + 952.00 + 4{,}626.00 - 2{,}284.70 = +467.55$$

So the adjustments earned 467.55, more than offsetting the 422.50 loss.

## What is left
$$-422.50 + 467.55 = +45.05$$

Interest on the cash flows (a gain of 56.21 on the stock sale proceeds, a cost of 5.75 on the option purchase, a net cost of 5.27 on the adjustments) takes us to a total of $+90.24$, and discounting to today gives $+89.21$. That is the topic of [[concepts/08-dynamic-hedging/hedge-pnl-components-and-discounting]].

## Common confusions
- **The original hedge is a loser here but that does not matter.** In a different path it could win and the adjustments could lose. The book: "it is impossible to determine beforehand which components will be profitable and which will not". What the model says is that, in some combination, you end up near the predicted profit. [[concepts/08-dynamic-hedging/hedge-pnl-components-and-discounting]]
- **Where does 37.62% come from?** From the 10 prices in the table: they *are* a path whose annualized volatility is 37.62% (calculation in the book's Appendix B). It is a crystal-ball number, set to make the example work; we can never know it in advance.
- **The week-by-week deltas come from the model, not the market.** Each week the book re-feeds the new price, the shorter time, 6% interest and the *same* 37.62% volatility into Black-Scholes. We reproduced them to within rounding.
- **No option trading after the start.** We never trade options again until expiration. Only the underlying's price movement drives the result.

## Related
- Chapter: [[chapters/08-dynamic-hedging]]
- Previous: [[concepts/08-dynamic-hedging/delta-neutral-adjustments]]
- Next: [[concepts/08-dynamic-hedging/hedge-pnl-components-and-discounting]]
- Code: [[code/dynamic_hedging.ipynb]]
- Maths needed: [[00-maths-refresher/signs-and-running-totals]], [[00-maths-refresher/simple-interest-and-time-fractions]]
- See also: [[glossary]], [[formulas]]
