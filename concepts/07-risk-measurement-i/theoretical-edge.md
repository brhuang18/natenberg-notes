# Theoretical edge

**One-line definition:** the theoretical edge of a trade is how much better than the model's theoretical value you traded: positive when you buy below value or sell above it.

## Intuition
A casino has a small edge on every bet. Over many bets, probability delivers it a profit even though any single bet can lose. An option trader tries to build the same position: a positive theoretical edge ([[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]). This does not guarantee profit on any one trade, but it puts the laws of probability on your side.

## The maths
Per option:

$$\text{edge (bought)} = \text{theoretical value} - \text{price paid} \qquad \text{edge (sold)} = \text{price received} - \text{theoretical value}$$

Both are the same formula if we use $+$ for buying and $-$ for selling:

$$\text{edge} = \text{quantity} \times (\text{theoretical value} - \text{price})$$

For an **underlying** contract the theoretical value is, by definition, the price at which you traded it, so its edge is always 0. Total edge is the sum over all options in the position.

## Worked example: Position 1
Sold 10 June 95 calls at 8.55; theoretical value 8.33.
- Edge per option $= 8.55 - 8.33 = +0.22$.
- Ten options: $10 \times 0.22 = +2.20$.
- The 7 underlying contracts bought at the market price: edge $0$.
- **Total edge $+2.20$.**

## Position 2: a negative edge is not (necessarily) a misprint
The book says: Position 2 (long 10 June 100 calls and 10 June 100 puts) has a negative edge, "This is not a misprint". It shows $-2.10$. If the inputs are right, the strategy loses money in the long run. No trader would intentionally open such a position, but the market keeps moving and a position that looked fine can later become one with negative edge. When that happens, a trader will try to close it, because the longer it is held the more likely a loss.

**Our check.** With the prices printed in Figure 7-13 (call 5.35, put 4.35, theoretical values 5.44 and 4.45), buying both would have a **positive** edge: $10 \times (5.44 - 5.35) + 10 \times (4.45 - 4.35) = +1.90$. To get $-2.10$ the prices must be 5.55 and 4.55, which is also what Figure 7-14 uses in positions 4 and 5 (see [[concepts/07-risk-measurement-i/reading-a-position-risk-table]]). So the intended negative edge is correct, but the 100-strike *prices* in Figure 7-13 look like a typo.

## Hedging and deliberate negative edge (footnote 12)
In theory a trader never starts with a negative edge. But once a position exists, a trader sometimes executes a trade with negative edge to make the remaining profit more secure. That is the whole objective of hedging: give up a little theoretical profit to cut risk.

## Common confusions
- **Edge is not expected profit per day.** It is the profit the model expects *if all inputs are right and the position is run to expiration with proper hedging* ([[chapters/05-theoretical-pricing-models]], Chapter 8).
- **Edge depends on your volatility estimate.** A different volatility gives a different theoretical value, so a different edge. See [[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]].
- **Edge first, then risk.** The book's order: check the edge, then read the risk measures.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/risk-measures-of-the-underlying-and-signs]]
- Next: [[concepts/07-risk-measurement-i/reading-a-position-risk-table]]
- See also: [[glossary]], [[formulas]]
