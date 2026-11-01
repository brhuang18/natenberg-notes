# Hedging an option with other options (what a volatility spread is)

**One-line definition:** a **volatility spread** is a position where the delta of some options is cancelled by **other options** (instead of by the underlying), leaving a position that is roughly delta neutral but still sensitive to the underlying's movement, to implied volatility and to time.

## Intuition
In Chapter 8 you bought an underpriced option and cancelled its delta with the underlying (a dynamic hedge). But the underlying is not the only thing with delta. Other options have delta too. You can cancel the delta of the options you like with the delta of other options.

Suppose a call with delta 50 looks underpriced. You buy 10 of them: $+500$ deltas. To neutralise $+500$ you could:

| Way to hedge | Result |
|---|---|
| Sell 5 underlying contracts | the Chapter 8 hedge: $-500$ |
| Buy puts with a total delta of $-500$ | a straddle-like position |
| Sell *different* calls with a total delta of $-500$ | a ratio spread, call spread, or similar |
| A mix of the above | any combination, as long as the total delta is $-500$ |

Each method gives a different position, but they share four features (page 169):

1. **Approximately delta neutral.**
2. **Sensitive to the underlying's movement** (gamma).
3. **Sensitive to implied volatility** (vega).
4. **Sensitive to the passage of time** (theta).

Spreads with these features are called **volatility spreads**. The rest of Chapter 11 looks at the common types: straddles, strangles, butterflies, condors, ratio spreads, Christmas trees, calendar spreads, time butterflies and diagonals.

## Why the choice of hedge matters
Hedging with the underlying leaves you with a pure gamma and vega position of one sign. Hedging with other options lets you **shape** the risk: how much gamma, how much vega, how fast the position decays, and what happens at the extremes (limited or unlimited). That shaping is the whole subject of this chapter.

## Common confusions
- **"Delta neutral" is a starting condition, not a promise.** The deltas change as the market moves or time passes ([[concepts/11-volatility-spreads/adjusting-a-volatility-spread]]).
- **If delta gets large, it stops being a volatility spread.** When directional considerations dominate volatility considerations, the position is a directional bet (page 197).
- **Hedging with the underlying has no gamma to offset**, which is why the Chapter 8 hedge was a pure gamma position ([[concepts/10-introduction-to-spreading/option-spreads-delta-gamma-vega-rho]]).

## Related
- Chapter: [[chapters/11-volatility-spreads]]
- Next: [[concepts/11-volatility-spreads/straddles-and-strangles]]
- Earlier: [[concepts/08-dynamic-hedging/option-replication-and-the-hedging-principle]], [[concepts/08-dynamic-hedging/delta-neutral-adjustments]], [[concepts/07-risk-measurement-i/delta]]
- See also: [[glossary]], [[formulas]]
