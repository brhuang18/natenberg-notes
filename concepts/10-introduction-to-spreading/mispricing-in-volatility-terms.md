# Relative mispricing, measured in volatility terms

**One-line definition:** in option markets a mispricing is usually expressed not as "the price is X too high" but as "the implied volatility is Y points above my estimate", because volatility is a common scale that lets you compare options of different strikes and expirations.

## Intuition
Suppose two shops each sell you an item. One is 1.00 too dear, the other 0.75 too dear. Which is the worse deal? If one item is a 10-cent pencil and the other a 5000-dollar TV, the *price gap* tells you nothing without knowing the *size of the item*. Options are like that: an option's price changes by different amounts for the same change in volatility depending on its strike and time (its vega). So "1.00 over" for one option and "0.75 over" for another are not comparable. Volatility points are.

## The maths
At a theoretical volatility $\sigma_{\text{theo}}$ every option has a theoretical value. The market price implies a volatility $\sigma_{\text{imp}}$ ([[concepts/06-volatility/implied-volatility]]). Define

$$\text{mispricing (price terms)} = \text{price} - \text{theoretical value}$$

$$\text{mispricing (volatility terms)} = \sigma_{\text{imp}} - \sigma_{\text{theo}}$$

An overpriced option has an implied volatility above $\sigma_{\text{theo}}$; an underpriced one has an implied volatility below it.

## Worked example (page 166)
Theoretical volatility 23%.

| Option | Theoretical value (at 23%) | Price | Overpriced by | Implied volatility | Volatility points over 23% |
|---|---|---|---|---|---|
| First | 7.00 | 8.00 | 1.00 | 26% | 3 |
| Second | 6.00 | 6.75 | 0.75 | 28% | 5 |

By **price** the first option looks more overpriced (1.00 against 0.75). By **volatility** the second is more overpriced (5 points against 3). A volatility trader would say the second is the better one to sell.

**Our reading (not in the book).** The ratio of the price gap to the volatility gap is roughly the option's vega (value change per volatility point, averaged between 23% and the implied volatility):

$$\text{first: } \frac{1.00}{3} \approx 0.33 \text{ per point} \qquad \text{second: } \frac{0.75}{5} = 0.15 \text{ per point}$$

The first option is about twice as sensitive to volatility, which is why it can be 1.00 over in price but only 3 points over in volatility. (They are probably different strikes or different expirations; a longer-dated near-the-money option has a larger vega, [[concepts/09-risk-measurement-ii/vega-in-different-conditions]].)

## Why this matters for spreads
A trader who thinks one option is overpriced and a related one is fairly priced can **sell the first and buy the second** (against each other, the volatility spread of Chapter 11). He cannot know the exact value of either contract, but he may be able to estimate the *relative* value, and when market prices differ from that relative value he buys or sells the spread. This is the same logic as the futures calendar spread, where the trader cannot tell which month is wrong but knows the gap is too big. [[concepts/10-introduction-to-spreading/cash-and-carry-and-calendar-spreads]]

## Common confusions
- **Both options are overpriced.** The comparison is about *how much*, not which is expensive. Both have implied volatility above 23%.
- **Implied volatility is not "a price".** It is the volatility you must feed into the model to get the market price out. [[concepts/06-volatility/implied-volatility]]
- **The vega reading is approximate.** Vega changes with volatility, so dividing the price gap by the volatility gap gives an average, not an exact vega. [[concepts/07-risk-measurement-i/vega]]

## Related
- Chapter: [[chapters/10-introduction-to-spreading]]
- Previous: [[concepts/10-introduction-to-spreading/option-spreads-delta-gamma-vega-rho]]
- Next: [[concepts/10-introduction-to-spreading/margin-for-error-and-trade-size]]
- Earlier: [[concepts/06-volatility/implied-volatility]], [[concepts/07-risk-measurement-i/theoretical-edge]]
- See also: [[glossary]], [[formulas]]
