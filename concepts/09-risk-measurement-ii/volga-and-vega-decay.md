# Volga (vomma) and vega decay

**One-line definition:** **volga** (also **vomma**) is how much an option's vega changes when volatility moves one point; **vega decay** is how much its vega changes as a day passes. Volga is largest for calls with deltas of about 10 and 90; vega decay is negative for every option and largest in size for short-dated options.

## Intuition
Vega is the slope of "option value against volatility". Is that line straight or curved?
- **At the money** it is nearly straight, so vega barely changes: volga is about 0.
- **Out and in the money** it curves upward: the option is nearly worthless at low volatility, then wakes up. Each extra volatility point adds more than the last. That "speeding up" is the volga.

*Name.* Both volga and vomma are contractions of "volatility gamma": the gamma (curvature) with respect to volatility rather than to the underlying price. (The book writes the phrase twice in a row; it is a duplicated phrase, not two different meanings.)

Vega decay is simply that vega **shrinks as time passes**: fewer days left means volatility has less time to matter.

## The maths
$$\text{volga} = \frac{\text{change in vega}}{\text{1 volatility point}} \qquad \text{vega decay} = \frac{\text{change in vega}}{\text{1 day passing}}$$

![Volga and vega decay against call delta](../../images/ch09-volga-and-vega-decay.png)

**Volga** (left panel, calls; puts mirror):
- About 0 at the money (call delta near 50).
- Largest for call deltas around **10 and 90**. Our model puts the peaks at about 8 and 93.
- **Bigger with more time**: at delta 10, the 1-year curve is about twice the 3-month curve, which is about twice the 1-month curve. Long-dated options have greater volga than short-dated ones.
- Bigger in a low-volatility market (the book's summary lists "low volatility").
- Positive for in- and out-of-the-money options, so their vega rises with volatility ([[concepts/09-risk-measurement-ii/vega-in-different-conditions]]).

**Vega decay** (right panel): negative everywhere (vega falls each day). It is roughly flat for deltas between 10 and 90 and drops toward zero at the extremes, so the options whose vega is most sensitive to the passing of time are those with deltas between about 10 and 90, with the largest in size around 15 to 20 and 80 to 85. It is bigger when little time is left: at the money, vega decays $-0.0005$ per day with a year left, $-0.0011$ with three months and $-0.0019$ with one month.

## Worked example
A 110 call, underlying 100, 91 days, volatility 25%: value 1.676, vega 0.1558, volga 0.0036. If volatility rises 5 points to 30%:

| Method | Calculation | Estimate |
|---|---|---|
| Vega only | $5 \times 0.1558$ | $+0.779$ |
| Vega plus volga | $0.779 + \tfrac12 \times 0.0036 \times 5^2$ | $+0.824$ |
| Model | $2.493 - 1.676$ | $+0.818$ |

If volatility **falls** 5 points to 20%: vega only $-0.779$; with volga $-0.779 + 0.045 = -0.734$; model $-0.725$. The $\tfrac12 \times \text{volga} \times (\Delta\sigma)^2$ term works just like $\tfrac12 \times \Gamma \times (\Delta S)^2$ in [[concepts/07-risk-measurement-i/estimating-option-value-with-delta-and-gamma]]. (This extension is our own, not printed in the book.)

**Why it matters.** With positive volga, a long option position gains **more** when volatility rises than its vega predicts and loses **less** when volatility falls; a short position is the reverse. The book uses this idea in Chapter 21: a position's vega-based estimate of its breakeven volatility is 34.90%, yet the graph crosses at about 36%, which it blames on the position's positive volga (the line curves upward). Compare [[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]].

## Common confusions
- **Volga is not vega.** Vega is the slope; volga is the *bend* of the same curve.
- **A "close to 0" volga at the money is not "no volatility risk".** It means the vega is steady there; the vega itself is largest.
- **Vega decay and volga respond to different inputs** (time and volatility), but they point the same way: more volatility *or* more time raises the vega of an in- or out-of-the-money option ([[concepts/09-risk-measurement-ii/time-and-volatility-have-similar-effects]]).

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/sensitivity-of-a-sensitivity]]
- Previous: [[concepts/09-risk-measurement-ii/vega-in-different-conditions]]
- Next: [[concepts/09-risk-measurement-ii/gamma-in-different-conditions]]
- See also: [[glossary]], [[formulas]]
