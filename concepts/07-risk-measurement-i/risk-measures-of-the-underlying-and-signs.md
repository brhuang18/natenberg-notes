# Risk measures of the underlying, signs, and adding them up

**One-line definition:** the underlying contract has delta 100 and every other risk measure 0; options have predictable signs; and every risk measure for a *position* is the sum of (quantity times measure) over its pieces.

## Intuition
Everything in a portfolio is measured in the same units: "how much does the position change if X changes by one unit?". Changes simply add up. A stock position is just the simplest case: it only responds to price direction.

## The underlying contract
| Measure | Value | Why |
|---|---|---|
| Delta | 100 (1.00) | gains or loses at exactly the rate of the underlying |
| Gamma | 0 | delta is always 100, so it never changes |
| Theta | 0 | the underlying does not decay |
| Vega | 0 | it is not subject to volatility considerations |
| Rho | 0 | interest rates do not directly change the underlying's value (footnote: they may change the forward price, but that is not the underlying's value to an option trader) |

The only risk measure of the underlying is delta; everything else is 0. Short underlying has delta $-100$.

## Signs for each position (Figure 7-12)
Derived from the single-option rules and the underlying row. "Stock" and "futures" in the rho column refer to the option's underlying, with stock-type settlement for futures options.

| If you are... | Delta | Gamma | Theta | Vega | Rho |
|---|---|---|---|---|---|
| Long underlying | + | 0 | 0 | 0 | 0 |
| Short underlying | $-$ | 0 | 0 | 0 | 0 |
| Long calls | + | + | $-$ | + | + (stock), $-$ (futures) |
| Short calls | $-$ | $-$ | + | $-$ | $-$ (stock), + (futures) |
| Long puts | $-$ | + | $-$ | + | $-$ (stock), $-$ (futures) |
| Short puts | + | $-$ | + | $-$ | + (stock), + (futures) |

Notes:
- **Gamma and vega are positive for all long options** and negative for all short options, calls or puts.
- **Gamma and theta have opposite signs** ([[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]]).
- **Reading in the project PDF:** the extracted figure appears to list "+" for delta of a short underlying and "$-$" for the rho of short puts on stock. Both look like misprints; the table above follows the logic (short stock has negative delta; short puts are the opposite of long puts).
- If options on futures are subject to futures-type settlement, rho is zero.

## Adding up (Figure 7-14 method)
For a position of several pieces:

$$\text{total measure} = \sum (\text{contracts, with } + \text{ for bought and } - \text{ for sold}) \times (\text{measure per contract})$$

Example: delta of Position 1 ($-10$ 95 calls with delta 71, $+7$ underlying contracts):

$$-10 \times 71 + 7 \times 100 = -710 + 700 = -10$$

The underlying contributes only delta; all its other terms are 0.

## Common confusions
- **Units.** In Figures 7-13 and 7-14 each option is on 100 shares and deltas are whole numbers: a delta of 56 means the option behaves like 0.56 of one underlying contract (56 shares).
- **Sign of a short position:** a short call has negative delta *and* negative gamma and positive theta. Mixed signs come from multiplying by a negative quantity.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/rho]]
- Next: [[concepts/07-risk-measurement-i/theoretical-edge]]
- See also: [[glossary]], [[formulas]]
