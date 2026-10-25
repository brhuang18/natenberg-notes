# Gamma and theta: you cannot have both

**One-line definition:** gamma and theta almost always have opposite signs, and their sizes go together: movement helps (positive gamma) or time passing helps (positive theta), but not both.

## Intuition
Long options are a bet on movement. You pay for that bet through time decay. If the market moves enough, the gamma gain beats the theta cost; if it sits still, you only pay. Short options are the opposite: you collect time decay as long as the market stays quiet and pay if it moves.

| | Gamma | Theta | You win when... |
|---|---|---|---|
| Long options | positive | negative | the market moves a lot |
| Short options | negative | positive | the market stays quiet |

## What the numbers show
**Single options (Figure 7-13).** Gamma and theta peak in the same place, near the money, and are smaller far away:

| Call strike | Gamma | Theta |
|---|---|---|
| 90 | 2.0 | $-0.029$ |
| 95 | 2.8 | $-0.034$ |
| 100 | 3.2 | $-0.035$ |
| 105 | 3.1 | $-0.032$ |
| 110 | 2.6 | $-0.027$ |

A large gamma comes with a large theta (of opposite sign), a small gamma with a small theta.

**Positions (Figure 7-14, with the corrected Position 4).**

| Position | Gamma | Theta |
|---|---|---|
| 1 (short calls, hedged) | $-28$ | $+0.34$ |
| 2 (long straddle) | $+64$ | $-0.54$ |
| 3 | $-25$ | $+0.23$ |
| 4 | $+12$ | $-0.06$ |
| 5 | $+4$ | $-0.02$ |

Every row has opposite signs, and larger gamma goes with larger theta.

## Where does Position 1's profit come from?
If the stock stays near 99.50, a negative gamma position is *happy*. The profit comes from the theta of $+0.34$: about 0.34 per day with no movement. That is the book's principle: theta is where a short-gamma position earns its keep.

## Exceptions (footnote 11)
Interest rates can occasionally produce a position with gamma and theta of the same sign. The numbers are usually very small. (Remember positive theta from negative time value, [[concepts/07-risk-measurement-i/theta]].)

## Why they are linked (a pointer, not a derivation)
The book does not derive this here. For a stock with no dividend the Black-Scholes equation says, with theta per *year*:

$$\Theta + r\,S\,\Delta + \tfrac12\,\sigma^2 S^2\,\Gamma = r\,V$$

where $V$ is the option value. The $\Gamma$ term is the largest, so theta is driven mainly by $-\tfrac12\sigma^2 S^2 \Gamma$ (with smaller interest terms): time decay and curvature are two faces of the same thing. For the June 100 call in Figure 7-13: $0.06 \times 5.435 - 0.06 \times 99.5 \times 0.5565 - 0.5 \times 0.25^2 \times 99.5^2 \times 0.0318 = 0.326 - 3.322 - 9.84 = -12.84$ per year, or $-0.035$ per day. This matches the table. We will return to this when the formula is covered.

## Common confusions
- **Gamma versus vega.** Gamma is about whether the underlying actually moves (realized volatility). Vega is about implied volatility. A short-gamma position wants a quiet market, a negative-vega one wants lower implied volatility: they often go together but not always ([[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]]).
- **"Positive theta" is not free money.** It is payment for taking the risk of a big move.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/reading-a-position-risk-table]]
- Next: [[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]]
- See also: [[concepts/07-risk-measurement-i/gamma]], [[glossary]], [[formulas]]
