# Clearinghouse and Counterparty Risk

**One-line definition:** on an exchange, the clearinghouse stands between every buyer and seller and guarantees both sides, so you do not need to trust whoever is on the other side of your trade.

## Intuition
If you buy from a stranger privately, you worry they won't deliver. On an exchange the link between you and the stranger is cut. The exchange (via its clearinghouse) becomes **the seller to you** and **the buyer from them**. If they default, the clearinghouse still honours your side.

## How a trade is cleared
1. Buyer and seller agree contract, quantity and price on the exchange floor or electronic network.
2. Each reports the trade to their own **clearing firm**.
3. The two clearing firms report to the **clearinghouse**.
4. If the two reports match, the trade is official. If not, both firms are told and the trade goes back to the buyer and seller to sort out.

## Layers of protection
| Layer | Role |
|---|---|
| Individual trader | Posts margin; must be associated with a clearing firm |
| Clearing firm | Guarantees its traders' obligations; collects margin and passes it to the clearinghouse (may ask traders for more than the clearinghouse requires) |
| Clearinghouse | Guarantees all trades; may reduce a firm's margin if its traders' long and short positions offset |

Individual traders and clearing firms occasionally fail, but a clearinghouse has never failed in the United States (per the book).

## Related
- Chapter: [[chapters/01-financial-contracts]]
- See also: [[concepts/settlement-margin-and-variation]]
