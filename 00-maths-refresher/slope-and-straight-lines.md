# Slope and straight lines

**One-line summary:** the slope of a straight line is "how much $y$ changes for each 1 step in $x$". If you know $y$ at one point and the slope, you can find $y$ anywhere along that line, and where it crosses zero.

Used in: [[concepts/04-expiration-profit-and-loss/slope-method-for-combined-positions]], [[concepts/04-expiration-profit-and-loss/expiration-pnl-and-breakeven]], [[concepts/04-expiration-profit-and-loss/complex-position-pnl-walkthrough]]

## Intuition
Think of walking along a road drawn on a graph. The slope tells you how steep the road is: +1 means you climb one metre for every metre you walk forward, -1 means you drop one metre, 0 means the road is flat.

In option graphs, $x$ is the **underlying price** and $y$ is the **position value** (or profit and loss). So the slope answers: "if the underlying goes up by 1, how much does my position gain or lose?"

## The maths

$$\text{slope} = \frac{\text{change in } y}{\text{change in } x}$$

**1. Walking along a line.** If the slope is $m$ and you move $\Delta x$ along the $x$-axis, then $y$ changes by $m \times \Delta x$:

$$y_{\text{new}} = y_{\text{old}} + m \times \Delta x$$

Example: P&L is $-3.00$ at 95 and the slope is $+1$. At 105 we have moved $\Delta x = 10$, so P&L $= -3.00 + 1 \times 10 = +7.00$.

**2. Where does the line cross zero?** Start at $(x_0, y_0)$ with slope $m$ and ask for the $x$ where $y = 0$:

| Step | What we do | Result |
|---|---|---|
| 1 | Write the walking rule and set $y = 0$ | $0 = y_0 + m \times (x - x_0)$ |
| 2 | Subtract $y_0$ from both sides | $-y_0 = m \times (x - x_0)$ |
| 3 | Divide both sides by $m$ | $-y_0 / m = x - x_0$ |
| 4 | Add $x_0$ to both sides | $x = x_0 - \dfrac{y_0}{m}$ |

Examples:
- $y_0 = -3.00$ at $x_0 = 95$, slope $+1$: $x = 95 - (-3)/1 = 98.00$.
- $y_0 = +7.00$ at $x_0 = 105$, slope $-2$: $x = 105 - 7/(-2) = 105 + 3.50 = 108.50$.

Only trust the answer if it lies **inside the stretch where that slope applies**. If the answer falls outside, the line has already changed slope before it reaches zero. A slope of 0 never reaches zero (unless it is already there).

**3. Adding slopes.** If a position is made of several pieces, each piece changes by its own slope $\times \Delta x$, so the combined change is the sum:

$$\text{slope of combination} = \text{slope}_1 + \text{slope}_2 + \dots$$

Owning several contracts multiplies the slope: 3 contracts that each have slope $+1$ give slope $+3$.

## Common confusions
- **Slope is not the value.** A line with slope $+1$ can sit at any height. The slope tells you the *rate of change*, not the level.
- **Sign of slope.** A negative slope means the position *loses* value when the underlying rises (and *gains* when it falls). A long put has slope $-1$ for exactly this reason.
- Division by the slope in the zero-crossing formula uses the sign too (see the second example above).

## Related
- Previous: [[00-maths-refresher/max-function]]
- Index: [[00-maths-refresher/README|Maths refresher]]
