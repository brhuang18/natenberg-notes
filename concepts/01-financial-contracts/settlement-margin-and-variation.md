# Settlement: Stock-Type vs Futures-Type (Margin and Variation)

**One-line definition:** settlement is how money and ownership actually move. *Stock-type*: pay in full now, profits stay on paper until you close. *Futures-type*: put down a small margin, then pay or receive profit and loss in cash every day.

## Intuition
- **Stock-type** is like buying something at a shop. You pay the full price. If it later rises in value, you are only richer *on paper* until you sell.
- **Futures-type** is like a daily bet that is settled every evening. The loser pays the winner each day, so wins and losses become real cash straight away.

## Stock-type settlement
Buy 100 shares at \$50: you pay $100 \times \$50 = \$5{,}000$ now. If the price rises to \$60 you have an *unrealized* (paper) profit of \$1,000. You only get to spend it by selling, which makes it *realized*.

Worked example (book Figure 1-1): buy 1,200 shares at \$53, sell 500 at \$57, hold 700 through a fall to \$51, then sell the last 700 at \$54.

| Step | Realized P&L | Unrealized P&L (on remaining shares) |
|---|---|---|
| Sell 500 at 57 | $(57-53)\times500 = +\$2{,}000$ | $(57-53)\times700 = +\$2{,}800$ |
| Price falls to 51 | +\$2,000 | $(51-53)\times700 = -\$1{,}400$ |
| Sell 700 at 54 | $+\$2{,}000 + (54-53)\times700 = +\$2{,}700$ | 0 |

## Futures-type settlement
No full payment: a futures contract is a forward, so nothing is exchanged up front. But both sides now have an obligation, so the exchange takes a **margin deposit** from each as security.

- **Margin**: a security deposit. It still belongs to the trader and can earn interest. Its size depends on the contract's notional value and how much the price might move.
- **Variation**: the daily credit or debit from price changes. Cash moves from the losing side's account to the winning side's every day.

Worked example (a long position):
- Contract: 1,000 units at \$75, so the notional value is \$75,000. Margin is \$3,000 each.
- Price rises to \$80. The buyer's variation credit is $(80-75)\times1000 = \$5{,}000$, taken from the seller.
- Price keeps rising to \$90 at maturity. The buyer pays $90 \times 1{,}000 = \$90{,}000$ for the goods, but has already received variation of $(90-75)\times1000 = \$15{,}000$.
- Net cost: $\$90{,}000 - \$15{,}000 = \$75{,}000$, which is exactly the original agreed price.

The daily cash flows are how the contract keeps the original price while the market moves.

## Why it matters for options
In North America, **all options are stock-type**: paid in full up front, profits unrealized until closed. That creates a trap with futures options:

- A futures position is **futures-type**: losses need cash *today*.
- A hedging option is **stock-type**: its offsetting gain is only *on paper*.

Even if the two exactly offset, you can face a cash shortfall and be forced to close early. Many exchanges outside North America avoid this by settling options the same way as their underlying.

## Common confusions
- Margin is **not** a payment for the contract. It is collateral, returned when the position is closed.
- Variation is real cash. Margin is held, variation is paid.
- Closing a futures position: either an offsetting trade (final variation paid, margin returned) or hold to maturity (physical delivery or, for indices, cash settlement).

## Related
- Chapter: [[chapters/01-financial-contracts]]
- See also: [[concepts/01-financial-contracts/clearinghouse-and-counterparty-risk]], [[glossary]]
