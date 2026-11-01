# Diagonal spreads

**One-line definition:** a **diagonal spread** is like a calendar spread, but the two options have **different exercise prices** as well as different expirations.

## Intuition
Draw a table with strikes across and expirations down. A **calendar** spread moves straight down a column (same strike, different month). A **diagonal** moves down *and* sideways (different strike, different month): hence the name.

Because both the strike and the month can vary, and the quantities can be unequal too, there are endless variations. The book says plainly that it is "almost impossible to generalize": **each diagonal must be analysed separately** (delta, gamma, theta, vega, and the payoff when the near option expires).

## The one case we can generalize
If a diagonal is:
1. done **one to one** (one far option per near option),
2. both options of the **same type** (both calls or both puts), and
3. both options have **about the same delta**,

then it behaves very much like an ordinary calendar spread.

Why? Equal deltas mean it is delta neutral without any ratio. Same-type options with the same delta are equally far from the money, so the *difference in decay speed* between the far and near option, and the *difference in vega*, are the same effects that drive a calendar spread: near option decays faster, far option has more vega.

Book examples (Figure 11-29; underlying 100, volatility 30%, June 4 months, April 2 months):

| Spread | Far option | Near option | Debit |
|---|---|---|---|
| Call diagonal | $+1$ June 115 call, 2.20 (delta 23) | $-1$ April 110 call, 1.60 (delta 23) | $2.20 - 1.60 = 0.60$ |
| Put diagonal | $+1$ June 80 put, 0.72 (delta $-8$) | $-1$ April 85 put, 0.48 (delta $-8$) | $0.72 - 0.48 = 0.24$ |

Look at the strikes: the **June strike is farther out of the money** than the April strike, yet the deltas match, because June has more time (more chance to get there). That is what lets the two deltas cancel at 1:1.

These out-of-the-money diagonals cost little and have small gamma, theta and vega; they are more modest versions of the at-the-money calendar spread.

## Common confusions
- **"Diagonal" is not one strategy.** It is a family; only the matching-delta case behaves like a calendar spread.
- **Same delta does not mean same strike.** Longer-dated options reach the same delta at a strike farther from the money.
- **If you ratio a diagonal, the generalization fails.** You are back to analysing it from scratch.

## Related
- Chapter: [[chapters/11-volatility-spreads]]
- Previous: [[concepts/11-volatility-spreads/calendar-spreads-interest-rates-and-dividends]]
- Next: [[concepts/11-volatility-spreads/long-short-premium-and-the-four-categories]]
- Earlier: [[concepts/11-volatility-spreads/calendar-spreads-time-decay]], [[concepts/07-risk-measurement-i/delta]]
- See also: [[glossary]], [[formulas]]
