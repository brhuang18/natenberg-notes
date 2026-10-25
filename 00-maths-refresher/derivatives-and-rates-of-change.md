# Derivatives and rates of change

**One-line summary:** a derivative is the slope of a curve at one point: how much the output changes per 1 step of the input. The risk measures (delta, gamma, theta, vega, rho) are all derivatives of the option value. The *second* derivative is the slope of the slope (gamma).

Used in: [[concepts/07-risk-measurement-i/delta]], [[concepts/07-risk-measurement-i/gamma]], [[concepts/07-risk-measurement-i/estimating-option-value-with-delta-and-gamma]], [[chapters/07-risk-measurement-i]]

## Intuition
[[00-maths-refresher/slope-and-straight-lines]] covered straight lines: the slope is the same everywhere. An option's value against the stock price is a **curve**, so the steepness changes from place to place. The derivative answers: "how steep is the curve *right here*?" Zoom in far enough on any smooth curve and it looks like a straight line; the derivative is that line's slope.

## The maths
**Average slope between two points** (any curve, any two points):

$$\text{average slope} = \frac{\text{change in } y}{\text{change in } x} = \frac{y_2 - y_1}{x_2 - x_1}$$

**Slope at one point (the derivative).** Make the gap between the two points smaller and smaller. The average slope settles down to a number: the derivative, written

$$\frac{dy}{dx} \qquad \text{(read: "change in } y \text{ per change in } x\text{")}$$

For an option with value $V$ and underlying price $S$:

$$\Delta = \frac{dV}{dS} \qquad \text{(delta)}$$

**Second derivative: the slope of the slope.** Take the derivative of the derivative:

$$\Gamma = \frac{d\Delta}{dS} = \frac{d^2 V}{dS^2} \qquad \text{(gamma, the curvature)}$$

A positive second derivative means the curve bends upward (like a smile); the slope is increasing.

**Partial derivatives.** The option value depends on several inputs: $V(S, t, \sigma, r)$. A *partial* derivative asks how $V$ changes when **one** input changes and **all the others are held fixed**. That is exactly the phrase "everything else unchanged" the book keeps using:

| Risk measure | Partial derivative of $V$ with respect to... |
|---|---|
| Delta | underlying price $S$ |
| Gamma | $S$ twice (the slope of delta) |
| Theta | time $t$ (value lost per day) |
| Vega | volatility $\sigma$ |
| Rho | interest rate $r$ |

**Using a slope to estimate a change.** Starting from a point with value $V$, slope $m$ and curvature $c$, moving the input by $h$:

$$V_{\text{new}} \approx V + m\,h + \tfrac12\,c\,h^2$$

The first correction uses only the slope (a straight line, the tangent). The second adds the bend. That is the "delta plus gamma" estimate.

## Worked example
**A curve you can check by hand: $y = x^2$.** At $x = 3$: $y = 9$. The slope of $x^2$ is $2x$ (a rule you can look up), so the slope at 3 is 6, and the curvature (slope of $2x$) is 2. Estimate $y$ at $x = 4$ ($h = 1$):

| Method | Estimate | True value 16 |
|---|---|---|
| Slope only | $9 + 6 \times 1 = 15$ | off by 1 |
| Slope plus curvature | $9 + 6 + \tfrac12 \times 2 \times 1 = 16$ | exact |

**From option values (June 100 call, stock 99.50, volatility 25%).** The model gives values at three prices:

| Stock | 98.50 | 99.50 | 100.50 |
|---|---|---|---|
| Call value | 4.8948 | 5.4353 | 6.0076 |

- Slope from 99.50 to 100.50: $(6.0076 - 5.4353)/1 = 0.572$. From 98.50 to 99.50: $0.540$.
- Slope at 99.50 (average of the two, a good approximation): $(0.572 + 0.540)/2 = 0.556$. The book's delta: 56 (0.56). ✓
- Change in slope per point: $0.572 - 0.540 = 0.032$. The book's gamma: 3.2 deltas per point (0.032). ✓

## Common confusions
- **You do not need to differentiate by hand.** In these notes, pricing software gives the derivatives. What you need is the meaning: "slope" and "slope of the slope".
- **A derivative is a *rate*, not a change.** Delta 0.56 does not say the option rises by 0.56; it says it rises by 0.56 *per 1.00 rise in the stock*, and only for small moves.
- **Units.** Gamma is "deltas per point". If delta is whole-numbered (56) and gamma is 3.2, a 1-point rise gives a delta of 59.2.

## Related
- Maths needed first: [[00-maths-refresher/slope-and-straight-lines]]
- Used in: [[chapters/07-risk-measurement-i]]
