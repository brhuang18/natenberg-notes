# Reading a position's risk table (Figures 7-13 and 7-14)

**One-line definition:** for a position with several options, add up each risk measure, then read the totals as "what do I want the market to do?"

## Intuition
With a handful of options you can eyeball the risk. With options at several strikes and expiries you cannot. The risk table is a quick summary: five numbers that say which direction, speed, time, volatility and rate moves help or hurt.

## The recipe
1. **Edge first.** Is the theoretical edge positive? ([[concepts/07-risk-measurement-i/theoretical-edge]])
2. **Add each risk measure:** quantity (+ bought, $-$ sold) times the measure from Figure 7-13, summed ([[concepts/07-risk-measurement-i/risk-measures-of-the-underlying-and-signs]]).
3. **Read the signs** with the book's Figure 7-15:

| Your position is... | You want... |
|---|---|
| Delta positive / negative | the underlying to rise / fall |
| Gamma positive / negative | big, fast moves / the market to sit still |
| Theta positive / negative | time to help (gain each day) / time to hurt |
| Vega positive / negative | implied volatility to rise / fall |
| Rho positive / negative | interest rates to rise / fall |

## The five positions in Figure 7-14 (recomputed from the Figure 7-13 table)
Stock 99.50, 91 days, volatility 25%, rate 6%.

| # | Position | Edge | Delta | Gamma | Theta | Vega | Rho |
|---|---|---|---|---|---|---|---|
| 1 | $-10$ 95 calls, $+7$ underlying | +2.20 | $-10$ | $-28$ | +0.34 | $-1.70$ | $-1.55$ |
| 2 | $+10$ 100 calls, $+10$ 100 puts | $-2.10$* | +120 | +64 | $-0.54$ | +3.92 | +0.03** |
| 3 | $+10$ 105 puts, $-20$ 95 puts | +5.80 | $-20$** | $-25$ | +0.23 | $-1.48$ | $-0.11$** |
| 4 | $+10$ 100 calls, $-10$ 90 calls | +2.30* | $-280$ | +12** | $-0.06$ | +0.74 | $-0.54$ |
| 5 | $-10$ 100 puts, $+20$ 105 puts, $-10$ 110 puts | +3.50* | $-30$ | +4 | $-0.02$ | +0.25 | $-0.04$ |

*Edge uses the 100-strike prices 5.55 and 4.55 (the Figure 7-13 prices 5.35 and 4.35 look like a typo; see below). **Differs from the book's printed total; see the errata.

## What each position wants
**Position 1** (short 95 calls hedged with long stock). Delta $-10$ is "delta neutral" for practical purposes. Gamma $-28$: wants a quiet market. Theta $+0.34$: earns about 0.34 a day if nothing moves. Vega $-1.70$: wants implied volatility to fall. Rho $-1.55$: wants rates to fall (the long stock is financed by a debit). The worst case: a swift upward move.

**Position 2** (long straddle). Delta $+120$ (slightly bullish; about 1.2 contracts). Gamma $+64$: wants big moves. Theta $-0.54$: pays about 0.54 a day. Vega $+3.92$: wants implied volatility to rise. Rho about 0. Negative edge: it is a bet on volatility being *higher* than 25%.

**Position 3** (long one 105 put per two short 95 puts: a put ratio spread). Delta $-20$, gamma $-25$, theta $+0.23$, vega $-1.48$: wants a quiet market and lower implied volatility, much like Position 1. Large positive edge (+5.80), mostly from selling the overpriced 95 puts (each $+0.21$).

**Position 4** (long 100 call, short 90 call: a bear call spread). Delta $-280$: bearish (like short 2.8 contracts). Small gamma, theta and vega: a mostly directional position.

**Position 5** (short 100 and 110 puts, long two 105 puts: a put butterfly). Everything is small: delta $-30$, gamma $+4$, theta $-0.02$, vega $+0.25$, rho $-0.04$. A butterfly has low sensitivity to all inputs.

(Names like ratio spread, butterfly and bear spread belong to Chapters 10 to 12; the point here is only the arithmetic.)

## Errata: where the book's printed totals differ from the arithmetic
We recomputed every total from the book's own Figure 7-13 numbers ([[code/risk_measures.ipynb]]).

| Item | Book prints | Recomputed | Likely cause |
|---|---|---|---|
| Fig 7-13: June 100 call price / put price | 5.35 / 4.35 | 5.55 / 4.55 needed for Fig 7-14 edges | typo in Fig 7-13 prices (Fig 7-14 positions 2, 4, 5 all use the higher prices) |
| Fig 7-13: put 105 vega | 0.195 | 0.192 | typo (calls and puts share a vega; Fig 7-14 uses 0.192) |
| Fig 7-13: put 95 theta | $-0.0.19$ | $-0.019$ | typo |
| Position 2 rho | +0.30 | +0.03 ($1.24 - 1.21$) | arithmetic slip |
| Position 3 delta | $-10$ | $-20$ (model with unrounded deltas: $-18$) | rounding or slip |
| Position 3 rho | +0.11 | $-0.11$ ($-1.67 + 1.56$) | sign slip |
| Position 4 gamma | $-12$ | +12 ($+32 - 20$) | sign slip: both calls are long gamma minus short gamma |
| Position 1 breakeven volatility | 27.29% | 26.29% | see [[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]] |
| Formulas for estimating option value | $S_1 - S_2$ | $S_2 - S_1$ | sign slip, see [[concepts/07-risk-measurement-i/estimating-option-value-with-delta-and-gamma]] |

The corrected Position 4 gamma (+12) matters: it keeps the pattern that gamma and theta have opposite signs ([[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]]): with $-12$ and theta $-0.06$ the pattern would break.

## Common confusions
- **Risk measures are only first-order.** They describe small changes; large moves need re-evaluation (gamma helps; see [[concepts/07-risk-measurement-i/estimating-option-value-with-delta-and-gamma]]).
- **Numbers are always changing.** Prices, time and volatility move, so every measure and the edge drift. The table is a snapshot.
- **Paralysis through analysis.** The book warns against analysing every conceivable risk until you cannot trade. The measures *identify* risk; they do not remove it. The skill is deciding beforehand which risks are acceptable.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/theoretical-edge]]
- Next: [[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]]
- See also: [[glossary]], [[formulas]]
