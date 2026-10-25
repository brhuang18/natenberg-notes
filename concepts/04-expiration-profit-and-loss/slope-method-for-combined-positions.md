# The slope method for combined positions

**One-line definition:** to draw the parity graph of any position, work out the slope of each contract in each stretch of underlying prices, add them up stretch by stretch, then join the line segments.

## Intuition
A position made of many options and underlying contracts looks complicated. But between two neighbouring exercise prices each piece is just a straight line with a known slope, because every option is either in or out of the money across the whole stretch. Straight lines add: the slope of the whole is the sum of the slopes of the parts ([[00-maths-refresher/slope-and-straight-lines]]). So you only need a table.

## The rules
1. **Critical prices** are the exercise prices. The graph only bends there.
2. **Slope of each piece** (multiply by the number of contracts, with short = negative):

| Piece | Slope where it is out of the money | Slope where it is in the money |
|---|---|---|
| Long call | 0 | +1 |
| Short call | 0 | -1 |
| Long put | 0 | -1 |
| Short put | 0 | +1 |
| Long underlying | +1 everywhere | |
| Short underlying | -1 everywhere | |

A call is in the money **above** its exercise price; a put is in the money **below** it.

3. **Add up** the slopes in each stretch: below the lowest exercise price, between each pair, and above the highest.
4. **Join** the segments. Positions that include underlying contracts never bend at the underlying price: a long or short underlying position is a straight line ("the location of the underlying position is irrelevant to the parity graph"). Only options create bends, and only at exercise prices.

## Simple examples (from the book)
**Long call + long put at the same exercise price.**

| Stretch | Call | Put | Total |
|---|---|---|---|
| Below $X$ | 0 | -1 | **-1** |
| Above $X$ | +1 | 0 | **+1** |

Value rises whichever way the underlying moves away from $X$. This kind of position is sensitive to the *size* of the move rather than its *direction*.

**Long call + short put at the same exercise price.** Below $X$: $0 + 1 = +1$. Above $X$: $+1 + 0 = +1$. Slope $+1$ everywhere, exactly like a long underlying position ([[concepts/04-expiration-profit-and-loss/equivalent-positions]]).

## Worked example: the book's 8-option position
Position: -4 underlying; +3 65 calls; +2 65 puts; +2 70 calls; -4 70 puts; -6 75 calls; +3 75 puts; +4 80 calls; -2 80 puts.

| Contract | Below 65 | 65-70 | 70-75 | 75-80 | Above 80 |
|---|---|---|---|---|---|
| +3 65 calls | 0 | +3 | +3 | +3 | +3 |
| +2 65 puts | -2 | 0 | 0 | 0 | 0 |
| +2 70 calls | 0 | 0 | +2 | +2 | +2 |
| -4 70 puts | +4 | +4 | 0 | 0 | 0 |
| -6 75 calls | 0 | 0 | 0 | -6 | -6 |
| +3 75 puts | -3 | -3 | -3 | 0 | 0 |
| +4 80 calls | 0 | 0 | 0 | 0 | +4 |
| -2 80 puts | +2 | +2 | +2 | +2 | 0 |
| -4 underlying | -4 | -4 | -4 | -4 | -4 |
| **Total** | **-3** | **+2** | **0** | **-3** | **-1** |

How to read a couple of cells:
- *+2 65 puts, below 65*: the puts are in the money, a long put has slope $-1$, and there are 2 of them: $2 \times (-1) = -2$.
- *-4 70 puts, below 70*: a short in-the-money put has slope $+1$; four of them give $+4$. Above 70 they are out of the money, so 0.
- *-6 75 calls, 75-80*: a short in-the-money call has slope $-1$; six of them give $-6$.

Reading the totals: below 65 the slope is $-3$, so as the underlying falls the value *rises* without limit; above 80 the slope is $-1$, so as the underlying rises the value *falls* without limit. The book's conclusion: the potential profit on the downside and the potential loss on the upside are both **unlimited**. For positions this complex there is often no way to place the graph on a vertical axis from the slopes alone. It still tells you the *character* of the position. The next note shows how to place it using one P&L value: [[concepts/04-expiration-profit-and-loss/complex-position-pnl-walkthrough]].

## Common confusions
- **Short puts have slope $+1$** in the money: you lose when the underlying falls, so the line slopes up as the underlying rises.
- **Count contracts.** A total of $+3$ means three contracts' worth of slope, not three kinds of option.
- The slope changes only at exercise prices, never at the current underlying price.

## Related
- Chapter: [[chapters/04-expiration-profit-and-loss]]
- Before: [[concepts/04-expiration-profit-and-loss/parity-graphs]]
- Maths needed: [[00-maths-refresher/slope-and-straight-lines]]
- See also: [[glossary]]
