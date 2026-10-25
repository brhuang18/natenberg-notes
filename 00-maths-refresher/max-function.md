# The max function (maximum of two numbers)

**One-line summary:** $\max(a, b)$ means "whichever of $a$ and $b$ is larger". Option intrinsic values use it to say "never less than zero".

Used in: [[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]], [[chapters/03-contract-specifications-and-option-terminology]]

## Intuition
An option gives you a *right*, not an obligation. If using the right would lose you money, you simply do not use it, so the option can never be worth less than zero. The max function is the neat way to write that "floor at zero".

## The maths

$$\max(a, b) = \begin{cases} a & \text{if } a \ge b \\ b & \text{if } b > a \end{cases}$$

Examples: $\max(0, 5) = 5$, $\max(0, -15) = 0$, $\max(3, 3) = 3$.

Option intrinsic values (with $S$ = underlying price, $X$ = exercise price):

$$\text{call} = \max(0,\; S - X) \qquad\qquad \text{put} = \max(0,\; X - S)$$

How to evaluate one, step by step:
1. Work out the difference inside the bracket ($S - X$ for a call, $X - S$ for a put). It may be negative.
2. Compare it with 0 and keep the larger.

## Worked example
A 95 call ($X = 95$) and a 110 put ($X = 110$), from the book's table:

| $S$ | $S - X$ for the 95 call | Call: $\max(0, S-95)$ | $X - S$ for the 110 put | Put: $\max(0, 110-S)$ |
|---|---|---|---|---|
| 80 | $-15$ | 0 | 30 | 30 |
| 95 | 0 | 0 | 15 | 15 |
| 100 | 5 | 5 | 10 | 10 |
| 110 | 15 | 15 | 0 | 0 |
| 125 | 30 | 30 | $-15$ | 0 |

Picture: plotted against $S$, a call's value is flat at 0 and then rises at a slope of 1 once $S$ passes $X$ (a "hockey stick"). A put is the mirror image.

## Common confusions
- The max does not change positive numbers, it only replaces negative ones with 0.
- For a call, big $S$ is good. For a put, small $S$ is good. That is why the subtraction is flipped.

## Related
- Index: [[00-maths-refresher/README|Maths refresher]]
