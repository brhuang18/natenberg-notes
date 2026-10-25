# Vega

**One-line definition:** the vega is the change in an option's theoretical value for each 1 percentage point change in volatility.

## Intuition
Chapter 6 showed that a wider spread of prices raises every option's value. Vega puts a number on it: "if implied volatility rises one point, what is this option worth?" It is positive for both calls and puts, because both gain when volatility rises ([[concepts/07-risk-measurement-i/what-moves-option-values]]).

## The maths
$$\text{new value} \approx \text{old value} + (\text{change in volatility points}) \times \text{vega}$$

Example: an option worth 3.25 at 20% volatility with a vega of 0.15 is worth 3.40 at 21% and 3.10 at 19%.

**Names.** There is no universal term. "Vega" is the usual trader word (it starts with "v", for volatility); it is not a Greek letter. Academics use *kappa* ($\kappa$); the Greek letter *nu* ($\nu$) looks like a written "v" and is sometimes used for vega.

## What Figure 7-13 shows (stock 99.50, 91 days, volatility 25%)

| Strike | Call vega | Put vega |
|---|---|---|
| 90 | 0.122 | 0.122 |
| 95 | 0.170 | 0.170 |
| 100 | 0.196 | 0.196 |
| 105 | 0.192 | 0.192 (printed 0.195) |
| 110 | 0.163 | 0.163 |

- Calls and puts with the same strike and expiry have the **same vega**.
- Vega is largest near the money, small far in or out. This matches the first volatility principle in [[concepts/06-volatility/volatility-and-option-values]]: at-the-money options change the most *in points*.
- Check: the 100 call at 25% is worth 5.435 and at 26% is worth 5.631. The difference is 0.196, the vega.

## Worked example
Position 2 ($+10$ 100 calls, $+10$ 100 puts): vega $= 10 \times 0.196 + 10 \times 0.196 = +3.92$. A one-point rise in implied volatility gains about 3.92. Position 1 (sold 10 95 calls): $-10 \times 0.170 = -1.70$: a one-point rise loses about 1.70.

## Common confusions
- **Vega is about implied volatility, not realized.** It asks what option *prices* will imply. Gamma is the exposure to realized movement ([[concepts/07-risk-measurement-i/gamma]], [[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]]).
- **The put 105 vega "0.195" in Figure 7-13 looks like a misprint.** Calls and puts share a vega, and the position arithmetic in Figure 7-14 uses 0.192.
- **Vega moves.** A 20-point volatility move is not 20 times the vega; it is only a good estimate for small changes.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/theta]]
- Next: [[concepts/07-risk-measurement-i/rho]]
- Later: Chapter 9 (vega in more detail), Chapter 11 (volatility spreads)
- See also: [[concepts/06-volatility/implied-volatility]], [[glossary]], [[formulas]]
