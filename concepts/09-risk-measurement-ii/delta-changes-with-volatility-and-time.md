# Delta changes with volatility and time (and the implied delta)

**One-line definition:** a call's delta moves toward 50 when volatility or time to expiration rises, and away from 50 (toward 0 or 100) when either falls; so a position that is delta neutral today may not be neutral tomorrow even if the underlying does not move.

## Intuition
Delta is roughly the market's estimate of the chance a call finishes in the money ([[concepts/07-risk-measurement-i/delta]]).
- **Low volatility or little time:** an out-of-the-money call will probably stay out of the money (delta near 0); an in-the-money call will probably stay in the money (delta near 100). Everything is "decided".
- **High volatility or plenty of time:** anything can still happen. The out-of-the-money call has a real chance of getting in, the in-the-money call a real chance of getting out. Both deltas drift toward 50 (a coin toss).
- **At the money** is already a coin toss, so its delta barely moves. It stays slightly above 50, which the book attributes to the lognormal distribution the model uses ([[concepts/06-volatility/lognormal-distributions]]); the exact reason comes with the Black-Scholes formula in later chapters. Interest and dividends can shift it further by moving the forward price.

**Puts** are the mirror image: put deltas go toward $-50$ as volatility or time rises, and toward 0 or $-100$ as it falls.

## The maths
Nothing new to calculate: delta is read from a pricing model, which takes volatility and time as inputs. What matters is the direction. From [[code/risk_measures_ii.ipynb]] (underlying 100, no interest):

| Volatility | 90 call (in the money) | 100 call (at the money) | 110 call (out of the money) |
|---|---|---|---|
| 10% | 98.4 | 51.0 | 3.0 |
| 15% | 92.6 | 51.5 | 10.8 |
| 25% | 81.8 | 52.5 | 24.2 |
| 40% | 73.5 | 54.0 | 35.3 |
| 60% | 69.2 | 56.0 | 43.3 |

(91 days left.) And with time passing, at 25% volatility:

| Days left | 90 call | 100 call | 110 call |
|---|---|---|---|
| 180 | 75.4 | 53.5 | 32.5 |
| 90 | 81.9 | 52.5 | 24.0 |
| 30 | 93.4 | 51.4 | 9.8 |
| 7 | 99.9 | 50.7 | 0.3 |
| 3 | 100.0 | 50.5 | 0.0 |

![Delta against volatility and time](../../images/ch09-delta-vs-volatility-and-time.png)

**Figure 9-5 in words.** The usual delta curve (S-shaped, from 0 up to 100 as the underlying rises) gets **steeper around the exercise price** as time shrinks or volatility falls, until in the limit it is a vertical step: delta 0 below the strike, 100 above.

## The implied delta
Because delta depends on volatility, and the volatility over the option's life is unknown, **no trader can be sure a position is really delta neutral**. The volatility used to calculate delta is a guess. Many traders therefore use the **implied delta**: the delta calculated from the option's *implied* volatility. The cost: the delta now changes whenever implied volatility changes, even if the underlying does not move.

**The book's example.** A trader owns 40 calls with implied volatility 32% and an implied delta of 25 each, and sells 10 underlying contracts to hedge:

$$40 \times 25 - 10 \times 100 = 0$$

Implied volatility rises to 36%. The calls were out of the money, so their delta moves toward 50. The book says it becomes 30:

$$40 \times 30 - 10 \times 100 = +200$$

The position went from neutral to bullish (equivalent to 2 underlying contracts long) "even though no other market conditions changed". Step by step:
- Step 1: option deltas total $40 \times 30 = 1{,}200$.
- Step 2: the hedge is $-10 \times 100 = -1{,}000$ (sold, so negative).
- Step 3: $1{,}200 - 1{,}000 = +200$.

**Our check.** The 30 is a round number. For a 91-day call with delta 25 at 32%, a model gives about 28.1 at 36%, so the new position delta is $40 \times 28.1 - 1{,}000 \approx +123$. Same lesson, smaller size. ([[concepts/09-risk-measurement-ii/vanna-and-charm]] explains how to predict the shift.)

## Common confusions
- **Which volatility to use for delta?** The book says using implied volatility "is only one possible approach"; the alternative is your own forecast. Neither is "right"; the point is that the number is a guess ([[questions]]).
- **Time alone changes delta.** Even over a weekend with nothing else happening, an out-of-the-money option's delta falls and an in-the-money one's rises. Far from expiration the drift is small (the 110 call with 180 days left, delta 32.5, loses about 0.06 of a delta point per day); near expiration one day is a large fraction of the remaining life and the effect is big (the same call with 30 days left loses about 0.40 per day).
- **At the money can be above 50.** It is not an error: forward price and lognormal skew push it a little above.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/signs-and-running-totals]] (the position delta sum)
- Previous: [[concepts/09-risk-measurement-ii/time-and-volatility-have-similar-effects]]
- Next: [[concepts/09-risk-measurement-ii/vanna-and-charm]]
- Built on: [[concepts/07-risk-measurement-i/delta]], [[concepts/08-dynamic-hedging/delta-neutral-adjustments]]
- See also: [[glossary]], [[formulas]]
