# Option spreads: spreading delta, gamma, vega or rho

**One-line definition:** in options a "position" can mean exposure to *direction* (delta), to *how much the underlying moves* (gamma), to *implied volatility* (vega) or to *interest rates* (rho); an option spread takes opposing amounts of one of these so the value depends mainly on the *other* factors.

## Intuition
With a futures spread, a leg's "position" was simply direction: if the market rises, one leg gains and the other loses. An option has several separate sensitivities ([[concepts/07-risk-measurement-i/delta]], [[concepts/07-risk-measurement-i/gamma]], [[concepts/07-risk-measurement-i/vega]], [[concepts/07-risk-measurement-i/rho]]). That means a trader can hold **long one sensitivity and short another** and so choose exactly which part of the market to be exposed to.

Think of a mixing desk with four faders. A spread is a way of pushing one fader up and another one down so the sound you care about stays and the noise cancels.

## The four kinds, step by step
| Spread type | How you build it | What its value depends on |
|---|---|---|
| **Delta (directional) spread** | opposing but *unequal* delta positions in different contracts | the direction of the underlying |
| **Gamma spread** | long gamma in one option, short gamma in another | the **actual volatility** (how much the underlying really moves) |
| **Vega spread** | long vega in one option, short vega in another | changes in **implied volatility** |
| **Rho spread** | long rho in one option, short rho in another | changes in **interest rates** |

**The Chapter 8 hedge is a gamma spread.** In dynamic hedging we bought (or sold) options, then offset their *delta* with the underlying. The underlying has delta (100 per contract) but **no gamma**, so the delta cancels but the option's gamma stays. The whole position then had a net gamma (positive if we bought options, negative if we sold them). Its result depended on **how much the underlying moved, not in which direction**. That is exactly "a long gamma position in one instrument and a zero-gamma position in another". [[concepts/08-dynamic-hedging/series-of-bets-and-dynamic-hedging]]

**Dynamic vs static spreads.**
- **Dynamic**: you must adjust periodically (the Chapter 8 hedge needed weekly delta adjustments). [[concepts/08-dynamic-hedging/delta-neutral-adjustments]]
- **Static**: you set it up once and carry it to expiration with no adjustments. This is usually only done when the risk of the spread is **well defined and limited**.

## Worked example (ours, in words)
Buy a call with delta 50 and sell the underlying in the amount that cancels the delta (Chapter 8's hedge). Total delta is zero, so the direction of the underlying does not matter *to first order*. What is left is **long gamma and short theta**: you gain when the underlying moves a lot and lose a little each day it does not. That is a gamma spread, and it is a *bet on volatility*, not on direction. Chapters 11 to 14 build many more spreads from options alone and read their delta, gamma, theta, vega and rho. [[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]]

## Why options have so many spreads (the book's three reasons)
1. A **relative mispricing** between contracts. [[concepts/10-introduction-to-spreading/mispricing-in-volatility-terms]]
2. To build a position that **reflects a view** of market conditions (and limits the loss if the view is wrong). We saw such positions in Chapter 4. [[concepts/04-expiration-profit-and-loss/equivalent-positions]]
3. To **control risk** and protect against wrongly estimated model inputs. [[concepts/10-introduction-to-spreading/margin-for-error-and-trade-size]] and [[concepts/10-introduction-to-spreading/casino-spreading-and-short-term-bad-luck]]

## Common confusions
- **"Delta neutral" does not mean "no risk".** It means no *directional* exposure; gamma, vega and the rest are still there. (Chapter 9's lesson too: the numbers are for today's conditions, and "nothing remains constant".) [[chapters/09-risk-measurement-ii]]
- **A spread is not always built from options.** The hedge in Chapter 8 used options plus the underlying.
- **A static spread is not risk-free.** It just has well-defined, limited risk; you still need to know it before you trade.

## Related
- Chapter: [[chapters/10-introduction-to-spreading]]
- Previous: [[concepts/10-introduction-to-spreading/executing-a-spread]]
- Next: [[concepts/10-introduction-to-spreading/mispricing-in-volatility-terms]]
- Earlier: [[concepts/07-risk-measurement-i/delta]], [[concepts/07-risk-measurement-i/gamma]], [[concepts/07-risk-measurement-i/vega]], [[concepts/07-risk-measurement-i/rho]], [[concepts/08-dynamic-hedging/option-replication-and-the-hedging-principle]]
- See also: [[glossary]], [[formulas]]
