# Choosing a spread when all options look cheap or expensive

**One-line definition:** if implied volatility is **lower** than your estimate, every option looks underpriced and you should pick spreads with **positive vega**; if it is **higher**, every option looks overpriced and you should pick spreads with **negative vega**.

## Intuition
The ideal spread **buys cheap options and sells expensive ones**. Then it has a positive theoretical edge whatever its type. But often your view on volatility makes **all** options look cheap (or all expensive). You cannot buy the cheap ones and sell the expensive ones, because they are all cheap.

So you ask: of all the spreads I could do, which ones are net **buyers** of volatility (when everything is cheap) or net **sellers** (when everything is expensive)? That is exactly what the **sign of vega** tells you.

> **If implied volatility is low, look for spreads with a positive vega. If it is high, look for spreads with a negative vega.**

Spreads with positive vega are net buyers of options (+vega) so benefit when options are cheap; negative vega spreads net sell options, so benefit when options are expensive.

## The book's test (Figures 11-32 and 11-33)
The theoretical values and deltas are the same as the evaluation table (stock 100, 20%, 2 and 4 months, 6%). Prices now come from an **implied volatility of 17%** (cheap) or **23%** (expensive).

**At 17% only positive-vega spreads have positive edge:** long straddles and strangles; short butterflies and condors; ratio spreads long more than short (including short Christmas trees); long calendar spreads.

**At 23% only negative-vega spreads have positive edge:** short straddles and strangles; long butterflies and condors; ratio spreads short more than long (including long Christmas trees); short calendar spreads.

## Checking it with numbers (ours, using the April positions from Figure 11-31)
**Theoretical edge** of a position is $\sum \text{quantity} \times (\text{theoretical value} - \text{price})$, with theoretical values at 20% and prices at the implied volatility. A positive edge is good.

| April position | Vega | Edge if prices at 17% | Edge if prices at 23% |
|---|---|---|---|
| Long straddle ($+10$ 100 calls, $+10$ 100 puts) | $+3.20$ | **$+9.63$** | $-9.65$ |
| Short straddle ($-20$ 105 calls, $-10$ 105 puts) | $-4.50$ | $-13.08$ | **$+13.54$** |
| Long strangle ($+10$ 95 puts, $+10$ 110 calls) | $+2.20$ | **$+6.09$** | $-6.88$ |
| Short strangle ($-30$ 100 puts, $-40$ 105 calls) | $-10.80$ | $-31.88$ | **$+32.52$** |
| Long butterfly (95/100/105 calls) | $-0.50$ | $-1.87$ | **$+1.43$** |
| Short butterfly (100/105/110 puts) | $+0.40$ | **$+1.22$** | $-1.03$ |
| Call ratio, buy more ($+20$ 110, $-10$ 105) | $+0.50$ | **$+1.01$** | $-1.83$ |
| Call ratio, sell more ($+20$ 95, $-30$ 100) | $-2.40$ | $-7.64$ | **$+7.06$** |
| Long call Christmas tree (100/105/110) | $-0.90$ | $-2.23$ | **$+2.86$** |
| Short call Christmas tree (90/100/105) | $+2.50$ | **$+7.74$** | $-7.40$ |
| Long calendar (June/April 100 calls) | $+0.60$ | **$+1.90$** | $-1.91$ |

In every row the **sign of the edge matches the sign of the vega** (positive vega wins at 17%, negative vega at 23%), which is the rule. (The calendar row uses the same implied volatility in both months, our simplifying assumption.)

## Why not just do straddles then?
It looks as if the sensible choice is a long straddle or strangle when everything is cheap, or a short one when everything is expensive: both sides of the spread have a positive edge. They do, and the edges are the biggest in the table above. But straddles and strangles also have the **biggest** gamma and vega, so they are among the **riskiest** spreads (Chapter 13). So a trader will often prefer a ratio spread, butterfly or condor, **even if it means buying some overpriced options or selling some underpriced ones**, to trade a smaller edge for much smaller risk ([[concepts/10-introduction-to-spreading/margin-for-error-and-trade-size]]).

## Calendar spreads and changing implied volatility
Traditional models assume one fixed volatility over an option's life. But implied volatility changes over time, and calendar spreads are especially sensitive to it. The corollary (page 201):

> **Long calendar spreads** are likely to be profitable when implied volatility is **low but expected to rise**. **Short calendar spreads** when it is **high but expected to fall**.

Exception: a long calendar can be sensible in a high-implied-volatility market if you expect the underlying to stagnate while implied volatility stays high ([[concepts/11-volatility-spreads/calendar-spreads-volatility-and-opposite-wishes]]).

## Common confusions
- **Theoretical edge comes from prices versus your volatility, not from the spread type.** The type decides *which* side to be on.
- **Edge is not the whole story.** The book's own warning: theoretical edge is only a measure of what you expect if you are right.
- **A spread's market conditions are set by its structure, not by the price you traded at.** After you have the position, yesterday's price does not change what helps or hurts it (page 199).

## Related
- Chapter: [[chapters/11-volatility-spreads]]
- Previous: [[concepts/11-volatility-spreads/reading-the-spread-tables]]
- Next: [[concepts/11-volatility-spreads/adjusting-a-volatility-spread]]
- Earlier: [[concepts/07-risk-measurement-i/theoretical-edge]], [[concepts/10-introduction-to-spreading/mispricing-in-volatility-terms]], [[concepts/06-volatility/implied-volatility]]
- See also: [[glossary]], [[formulas]]
