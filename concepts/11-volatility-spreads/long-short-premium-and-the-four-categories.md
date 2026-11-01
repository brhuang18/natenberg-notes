# Long and short premium, and the four categories of volatility spread

**One-line definition:** a spread with **positive gamma** is **long premium** (helped by movement), one with **negative gamma** is **short premium** (helped by calm); and because volatility spreads are delta neutral and gamma and theta always have opposite signs, every spread falls into one of **four categories** according to the signs of gamma and vega.

## Intuition
"Premium" is the time value you pay or collect. If you **buy** options you are paying premium and hoping the underlying moves enough to earn it back: **long premium**. If you **sell** options you collect premium and hope the underlying stays quiet so you keep it: **short premium**.

You cannot have it both ways: if movement helps you, time hurts you; if movement hurts you, time helps you. That is the **gamma/theta trade-off** ([[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]]). Positive gamma always comes with negative theta; negative gamma with positive theta.

Vega is a separate dial: it measures whether you gain or lose when **implied** volatility changes.

## The four categories
Because a volatility spread is delta neutral and theta follows gamma, only **gamma** and **vega** are free to vary independently:

| Gamma | Vega | Conditions that help the position | Examples |
|---|---|---|---|
| $+$ | $+$ | volatile underlying; **rising** implied volatility | long straddle/strangle, short butterfly/condor, ratio spreads buying more than selling, short Christmas trees |
| $-$ | $-$ | quiet underlying; **falling** implied volatility | short straddle/strangle, long butterfly/condor, ratio spreads selling more than buying, long Christmas trees |
| $+$ | $-$ | volatile underlying; falling implied volatility | **short calendar spread** |
| $-$ | $+$ | quiet underlying; rising implied volatility | **long calendar spread** (and long time butterfly) |

The first two rows are "natural": realized and implied volatility help or hurt together. The calendar spreads are the exceptions ([[concepts/11-volatility-spreads/calendar-spreads-volatility-and-opposite-wishes]]).

## How big? (page 197-198)
Within each category, some spreads have large Greeks, some small ones:

- **Straddles and strangles:** the largest gamma and vega. Biggest profit when right, biggest loss when wrong.
- **Butterflies and condors:** the smallest. Smaller profit when right, smaller loss when wrong.
- **Ratio spreads and Christmas trees:** in between.

## Limited or unlimited? (Figure 11-30)
Delta is assumed to be about zero for all. $\dagger$ = the great majority of delta-neutral ratio spreads, which are a credit when buying more than selling and a debit when selling more than buying.

| Spread | Gamma | Theta | Vega | Downside | Upside |
|---|---|---|---|---|---|
| Long straddle | $+$ | $-$ | $+$ | unlimited reward | unlimited reward |
| Long strangle | $+$ | $-$ | $+$ | unlimited reward | unlimited reward |
| Short butterfly | $+$ | $-$ | $+$ | limited reward | limited reward |
| Short condor | $+$ | $-$ | $+$ | limited reward | limited reward |
| Call ratio, buy more | $+$ | $-$ | $+$ | limited reward$^\dagger$ | unlimited reward$^\dagger$ |
| Put ratio, buy more | $+$ | $-$ | $+$ | unlimited reward$^\dagger$ | limited reward$^\dagger$ |
| Short straddle | $-$ | $+$ | $-$ | unlimited risk | unlimited risk |
| Short strangle | $-$ | $+$ | $-$ | unlimited risk | unlimited risk |
| Long butterfly | $-$ | $+$ | $-$ | limited risk | limited risk |
| Long condor | $-$ | $+$ | $-$ | limited risk | limited risk |
| Call ratio, sell more | $-$ | $+$ | $-$ | limited risk$^\dagger$ | unlimited risk$^\dagger$ |
| Put ratio, sell more | $-$ | $+$ | $-$ | unlimited risk$^\dagger$ | limited risk$^\dagger$ |
| Long calendar | $-$ | $+$ | $+$ | limited risk | limited risk |
| Short calendar | $+$ | $-$ | $-$ | limited reward | limited reward |

(Christmas trees are described in the text as acting like strangles with one side limited; their rows follow the same pattern: long trees are $-/+/-$, short trees $+/-/+$, Figure 11-18.)

**How to use the table.** Look down the last two columns: *unlimited* appears only for straddles, strangles and the unlimited side of ratio spreads and trees. Everything else is a trade-off: the butterfly's limited risk is paid for by its limited reward.

## Delta neutral is approximate
A spread need not be exactly delta neutral. "In practice, a volatility spread should have a delta that is small enough that the directional considerations are less important than the volatility considerations" (page 198), often a subjective judgment. If delta becomes large, you are no longer in a volatility spread at all.

## Long and short: the naming rule
A spread executed at a **debit** (cash out) is **long**; at a **credit** (cash in) it is **short**. This is why the sign conventions in the evaluation tables show purchases as negative cash and sales as positive.

## Common confusions
- **"Premium" here is time value**, not the price you paid.
- **The "four categories" are about Greeks, not strategies.** Two spreads with the same signs can have very different sizes.
- **Positive vega is not the same as positive gamma.** Only calendar spreads separate them.
- **Unlimited is not the same as likely.** Both limited-risk and unlimited-risk positions should be judged by probability as well ([[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]).

## Related
- Chapter: [[chapters/11-volatility-spreads]]
- Previous: [[concepts/11-volatility-spreads/diagonal-spreads]]
- Next: [[concepts/11-volatility-spreads/reading-the-spread-tables]]
- Earlier: [[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]], [[concepts/07-risk-measurement-i/vega]]
- See also: [[glossary]], [[formulas]]
