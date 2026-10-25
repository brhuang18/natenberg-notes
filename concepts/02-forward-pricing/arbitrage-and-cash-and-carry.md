# Arbitrage and cash-and-carry

**One-line definition:** *arbitrage* is buying and selling the same (or very closely related) things in different markets to profit from an apparent mispricing. *Cash-and-carry* is the standard version for forwards: buy in the cash market, sell the forward, and carry the position to maturity.

## Intuition
If a market lets you buy something cheaply in one place and sell it for more in another, with the cost of getting it there smaller than the gap, you can make a profit with little or no risk. People who do this push the cheap price up and the dear price down until the gap disappears. That is why fair prices (like the forward price in [[concepts/02-forward-pricing/forward-price-cost-and-benefit]]) hold in practice.

Natenberg's definition is deliberately modest. A truly riskless profit is rare "because there is almost always something that can go wrong".

## The commodity example (why "same price" is not enough)
A commodity trades at \$700 in London and \$710 in New York. Buy in London, sell in New York: \$10 profit? Not necessarily. Shipping and transit insurance both cost money. If they add up to more than \$10 a unit, there is no profit. Professionals know these costs, so they can see immediately whether a gap is a real opportunity.

## Carry trades are *not* arbitrage
A "carry trade" borrows a low-interest currency to buy a high-interest one. It is sometimes called arbitrage, but the interest rates may change and the exchange rate is not fixed. If the foreign currency falls against the domestic one, repaying the loan costs more. Natenberg says the term is "probably misapplied".

## Cash-and-carry with a stock (the book's example)
Stock $S = 67.00$, maturity 8 months, rate 6%, expected dividends $D = 0.66$. The fair forward price is

$$F_{\text{fair}} = 67.00 \times (1 + 0.06 \times 8/12) - 0.66 = 69.68 - 0.66 = 69.02$$

The market is offering an 8-month forward at **69.50**, which is higher than fair. The forward is "too expensive", so **sell the forward and buy the stock.**

| When | Cash flow | Amount |
|---|---|---|
| Today | Borrow to buy the stock | +67.00 |
| Today | Buy the stock | -67.00 |
| Today | Sell the forward at 69.50 | 0 (no cash moves yet) |
| During the 8 months | Receive dividends | +0.66 |
| Maturity | Deliver the stock, receive the forward price | +69.50 |
| Maturity | Repay the loan | -67.00 |
| Maturity | Pay interest: $67.00 \times 0.06 \times 8/12$ | -2.68 |
| **Total** | | **+0.48** |

The book lists the same flows more briefly: borrowing cost $-2.68$, buying the stock $-67.00$, dividend $+0.66$, forward price received $+69.50$, total $+0.48$. It leaves out the loan itself because the 67.00 borrowed and the 67.00 repaid cancel. The total is **+0.48**, which equals $69.50 - 69.02$.

Why it is risk-free on price: the stock is bought at a known 67.00 and delivered at a known 69.50. Whatever the stock does in between does not change the profit.

## The reverse trade
If the market's forward price is **below** fair value, do the opposite: **buy the forward and sell the stock** (a "reverse cash-and-carry"). With the forward at 68.75 and fair value at 69.02, an owner of the stock who sells it, invests the proceeds at 6% and buys the forward makes $69.02 - 68.75 = 0.27$. Someone who does *not* own the stock must borrow it to sell short, which brings extra costs. That case is in [[concepts/02-forward-pricing/short-selling-and-borrowing-costs]].

## What can still go wrong
Natenberg lists risks even in a "riskless" strategy:
- **Interest rate risk.** Most traders borrow at a floating rate. If rates rise, interest costs rise and profit shrinks. (A fixed-rate loan removes this risk.)
- **Dividend risk.** Dividends not yet declared are only estimates. If the company cuts the dividend, profit falls.
- **Your own model may be wrong.** When the market disagrees with you, check your inputs before assuming a free lunch. The mismatch may mean your rate or dividend guess is off. That leads to [[concepts/02-forward-pricing/implied-values]].

## Common confusions
- Arbitrage profit does not depend on whether the market goes up or down. It depends on the *relationship* between prices.
- "Riskless" always has fine print: costs, rate changes, dividend changes.

## Related
- Chapter: [[chapters/02-forward-pricing]]
- See also: [[concepts/02-forward-pricing/forward-price-cost-and-benefit]], [[concepts/02-forward-pricing/forward-price-by-instrument]], [[glossary]]
