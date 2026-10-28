# The futures-option hedge: selling an overpriced put (Figures 8-4 and 8-5)

**One-line definition:** the same dynamic hedge, run the other way round: sell an option that is priced above its theoretical value, hedge with futures, and collect the difference; here the cash flows from the hedge are futures **variation** rather than stock purchases and sales.

## Intuition
In the stock example we bought something cheap and hedged it. Here we **sell** something expensive. Selling an overpriced put gives us cash now (1.70) for something worth only 1.46, so we start 0.24 ahead per put. The hedge's job is to keep that edge safe from the market's direction until the put expires.

Two things differ from the stock example. First, the hedge instrument is a **futures contract**. A futures position needs no cash to establish; instead each price change creates a cash credit or debit called **variation** ([[concepts/01-financial-contracts/settlement-margin-and-variation]]). Second, because we are *short* an option, the adjustments go the opposite way: we are forced to **sell after prices fall and buy after they rise**. That sounds backwards, and it is: it is the cost the seller of gamma pays, and it is financed by the time value the put loses.

## The setup
| Item | Value |
|---|---|
| Futures price | 61.85 |
| Time to March expiration | 10 weeks (70 days) |
| Interest rate | 8.00% |
| True volatility (crystal ball) | 21.48% |
| March 60 put | price 1.70 (implied volatility 23.92%), theoretical value 1.46, delta $-35$ |
| Position | sell 100 puts, sell 35 futures |

Delta check: 100 short puts with delta $-35$ each give $-100 \times (-35) = +3{,}500$ deltas (short puts have positive delta). Selling 35 futures gives $-35 \times 100 = -3{,}500$. Total 0. We recomputed value 1.46, delta $-35.0$ and implied volatility 23.92%.

The book assumes the options use **stock-type settlement** (full premium paid or received immediately, the U.S. convention). Futures always use futures-type settlement.

## Week by week (Figure 8-4, with our corrections)
Short futures in total includes the original 35. Variation is the price change times the number held during that week (a short position gains when the price falls); interest runs to expiration at 8%.

| Week | Futures | Put delta | Total delta before trade | Trade | Short in total | Variation | Interest |
|---|---|---|---|---|---|---|---|
| 0 | 61.85 | $-35$ | 0 | start | 35 | | |
| 1 | 60.83 | $-42$ | $+700$ | sell 7 | 42 | $+35.70$ | $+0.49$ |
| 2 | 62.78 | $-28$ | $-1{,}400$ | buy 14 | 28 | $-81.90$ | $-1.01$ |
| 3 | 63.16 | $-24$ | $-400$ | buy 4 | 24 | $-10.64$ | $-0.11$ |
| 4 | 61.68 | $-34$ | $+1{,}000$ | sell 10 | 34 | $+35.52$ | $+0.33$ |
| 5 | 59.86 | $-50$ | $+1{,}600$ | sell 16 | 50 | $+61.88$ | $+0.47$ |
| 6 | 62.88 | $-21$ | $-2{,}900$ | buy 29 | 21 | $-151.00$ | $-0.93$ |
| 7 | 61.50 | $-31$ | $+1{,}000$ | sell 10 | 31 | $+28.98$ | $+0.13$ |
| 8 | 62.60 | $-15$ | $-1{,}600$ | buy 16 | 15 | $-34.10$ | $-0.10$ |
| 9 | 60.18 | $-45$ | $+3{,}000$ | sell 30 | 45 | $+36.30$ | $+0.06$ |
| 10 | 58.61 | | | close out 45 | | $+70.65$ | 0 |

Two slips in the book's table, found by recomputing: week 7 variation is printed 29.98 but is $21 \times (62.88 - 61.50) = 28.98$; and the week 9 total delta position is printed $-3{,}000$ although a sell needs $+3{,}000$. The week 10 variation ($45 \times (60.18 - 58.61) = +70.65$) is not printed in the table but is part of the book's adjustment total.

**Examples from the book.** After week 1 the futures fell to 60.83, so the 35 shorts earned $35 \times (61.85 - 60.83) = +35.70$. We could earn 8% on that for the remaining 63 days: $35.70 \times 8\% \times 63/365 = +0.49$. At the end of week 1 we sold 7 more, so we were short 42. After week 2 the futures rose to 62.78: $42 \times (60.83 - 62.78) = -81.90$, financed for 56 days at 8%: $-81.90 \times 8\% \times 56/365 = -1.01$.

## The P&L components (Figure 8-5)
| Component | Calculation | Result |
|---|---|---|
| Original hedge, option | sold at 1.70, worth $60 - 58.61 = 1.39$ at expiration: $100 \times (1.70 - 1.39)$ | $+31.00$ |
| Original hedge, futures | $35 \times (61.85 - 58.61)$ | $+113.40$ |
| **Original hedge** | | $+144.40$ |
| **Adjustments** | total variation $(-8.61)$ minus the original futures P&L $(+113.40)$ | $-122.01$ |
| Carry on the options | we *received* $100 \times 1.70 = 170$: $170 \times 8\% \times 70/365$ | $+2.61$ |
| Interest on the variation | sum of the weekly interest column | $-0.67$ |
| **Total** | | $+24.33$ |
| Discounted | $24.33 / (1 + 0.08 \times 70/365)$ | $+23.96$ |
| Predicted | $100 \times (1.70 - 1.46)$ | $+24.00$ |

Three components are the same as the stock example (original hedge, adjustments, carry on the options). The interest on the stock position and on the adjustments is *replaced* by interest on the variation.

Notice the signs: this time the original hedge is the winner ($+144.40$) and the adjustments are the loser ($-122.01$), the mirror of the stock example. Time value decay on the put helps us, while the forced "sell low, buy high" adjustments cost us.

## Stock example and futures example side by side
| | Stock example | Futures example |
|---|---|---|
| Option trade | buy underpriced call | sell overpriced put |
| Edge per option | $5.89 - 5.00 = 0.89$ | $1.70 - 1.46 = 0.24$ |
| Option delta (per option held) | $+50$ | $-35$ (but short, so $+35$) |
| Hedge | short 50 stock contracts | short 35 futures |
| Cash at the start | pay 500 for options, receive 4,885 for stock | receive 170 for puts; nothing for futures |
| Ongoing cash | full price of each stock trade | variation = price change $\times$ futures held |
| Adjustments go | sell after rises, buy after falls | sell after falls, buy after rises |
| Profit comes from | adjustments beat the option's time decay | time decay beats the adjustments |
| Hedge wins if realized volatility is | above 32.40% | below 23.92% |
| Result today vs prediction | 89.21 vs 89.00 | 23.96 vs 24.00 |

## Common confusions
- **Why sell futures when the puts' delta is negative?** Each put loses value when the futures rise, but the *seller* of the put gains, which is a long-delta position. We offset a long-delta position by selling futures. ([[concepts/08-dynamic-hedging/delta-neutral-adjustments]])
- **Selling an option: more volatility is bad.** The put was sold at an implied volatility of 23.92%; if the futures actually move more than that, the forced adjustments cost more than the time decay earns, and we lose ([[concepts/08-dynamic-hedging/realized-volatility-and-the-race]]).
- **Futures have no theoretical value.** Like the stock in the first example, futures trades change delta but not the theoretical edge.

## Related
- Chapter: [[chapters/08-dynamic-hedging]]
- Previous: [[concepts/08-dynamic-hedging/implied-volatility-moves-and-holding-the-hedge]]
- Next: [[concepts/08-dynamic-hedging/option-replication-and-the-hedging-principle]]
- Earlier: [[concepts/01-financial-contracts/settlement-margin-and-variation]], [[concepts/07-risk-measurement-i/futures-and-currency-options-interest-rates]]
- Maths needed: [[00-maths-refresher/signs-and-running-totals]]
- Code: [[code/dynamic_hedging.ipynb]]
- See also: [[glossary]], [[formulas]]
