# How the vanna, charm, volga and vega decay graphs are made (and how to read them)

**One-line definition:** each graph is built by taking an option, nudging **one** input a little (volatility up one point, or one day forward), recording how much its delta or its vega changed, and plotting that change against the option's delta; reading it means checking which side of the zero line a point is on (the **sign**) and how far from the line it is (the **size**).

## Intuition
Figures 9-6, 9-7, 9-15 and 9-17 look alike: a hump on each side of delta 50. They are four different questions:

| Graph | Book figure | What changes | What we nudge | Question it answers |
|---|---|---|---|---|
| Vanna | 9-6 | delta | volatility, up 1 point | If volatility rises a point, how many delta points does this option's delta move? |
| Charm | 9-7 | delta | one day passes | If a day passes (nothing else changes), how far does delta move? |
| Volga | 9-15 | vega | volatility, up 1 point | If volatility rises a point, how much does the vega change? |
| Vega decay | 9-17 | vega | one day passes | If a day passes, how much does the vega change? |

Delta is on the x-axis because it puts every option on one scale: a 20-delta call is "equally far out of the money" whatever the strike, price or volatility, so one picture covers them all. (Puts mirror the calls, with deltas from $-100$ to 0.)

## The recipe
1. Pick a call delta, the x-axis value (say 20), and find the strike that gives it.
2. Work out the measure for that option: the delta (vanna, charm) or the vega (volga, vega decay).
3. Change **one** input a little: volatility up one point (the code goes half a point either side) or one day on.
4. Work out the measure again and subtract. That difference is one point on the graph.
5. Repeat for many deltas and join the points. Repeat with a different volatility or a different time left for each extra curve.

A computer does this in a few lines; the book's graphs are the same thing drawn from a pricing model. The code is in [[code/risk_measures_ii.ipynb]] (the cell "How a point on these graphs is made").

## Worked example: one point on each graph
A 20-delta call: underlying 100, strike 111.95, 91 days left, volatility 25% (no interest).

| Graph | Before | After | Difference (the point on the graph) |
|---|---|---|---|
| Vanna | delta 19.45 at volatility 24.5% | delta 20.54 at 25.5% | **+1.08** delta points per volatility point |
| Charm | delta 20.00 today | delta 19.85 tomorrow | **−0.15** delta points per day |
| Volga | vega 0.1375 at 24.5% | vega 0.1420 at 25.5% | **+0.0045** per volatility point |
| Vega decay | vega 0.1398 today | vega 0.1384 tomorrow | **−0.0014** per day |

Repeat the same four calculations for a 30-delta call, a 40-delta call and so on, and plot each column against delta: those are the four figures.

## Reading sign and size
- **Sign** (which side of the zero line): positive means the measure goes **up** when the input is nudged, negative means it goes **down**. Vanna $+1.08$: a rise in volatility lifts the delta. Charm $-0.15$: a day passing lowers it.
- **Size** (distance from the zero line): how big the change is. This is what grows or shrinks with volatility or time.
- **Size is the distance from the zero line, not the height on the page.** A curve that dips further below the line in the negative region is a *larger* effect, even though it is "lower".

Example: the vanna of a 20-delta and an 80-delta call at three volatilities (91 days).

| Volatility | 20-delta call | 80-delta call |
|---|---|---|
| 15% | +1.71 | −1.43 |
| 25% | +1.08 | −0.80 |
| 40% | +0.73 | −0.45 |

The signs never change (positive on the left, negative on the right), but at higher volatility the numbers are **closer to zero on both sides**: the curve is flatter. It is not "smaller on one side and bigger on the other." The book's remark that vanna "falls as we raise volatility and rises as we reduce volatility" is about size, and in the negative region "rises" has to be read as "gets more negative".

## The four shapes at a glance
| Graph | About zero near call delta | Biggest near call delta | Bigger size when | Why (short) |
|---|---|---|---|---|
| Vanna | 50 (a little above) | 15-20 and 80-85 | volatility is **low** | one volatility point is a larger share of a narrower spread |
| Charm | 50 (a little above) | 15-20 and 80-85 | **little time** is left | one day is a larger share of a shorter life |
| Volga | 50, and 0 and 100 | about 10 and 90 | **more time** is left | the bend in "option value against volatility" |
| Vega decay | 0 and 100 only (a broad plateau between about 10 and 90) | about 15-20 and 80-85 | **little time** is left | fewer days left, plus drifting away from the money |

Details: [[concepts/09-risk-measurement-ii/vanna-and-charm]] and [[concepts/09-risk-measurement-ii/volga-and-vega-decay]].

## Sign convention against the book (the two time-based graphs)
The book's formulas differentiate with respect to time *to* expiration, so its Figure 9-7 (charm) shows the effect of one day **more** time. Ours show a day **passing**, so the signs are opposite: the book draws charm with a positive hump at call delta 20, ours is negative there. Turn one upside down and they agree; the shapes and sizes are identical. The same applies to vega decay (Figure 9-17). Vanna and volga have no such flip, because volatility is not time.

## Common confusions
- **"The high-volatility curve is less on both sides."** It is closer to the zero line on both sides, which means a smaller size; see above.
- **Each curve is a snapshot.** It is drawn for one volatility and one time left (the curve label). It does not show what happens to a particular option as time passes.
- **Vanna $+1.08$ is not "108%".** It means about one delta point per volatility point (delta in whole numbers).
- **A flat curve does not mean "no risk".** It means this sensitivity of a sensitivity is small; delta and vega themselves are not affected.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/sensitivity-of-a-sensitivity]]
- Used by: [[concepts/09-risk-measurement-ii/vanna-and-charm]], [[concepts/09-risk-measurement-ii/volga-and-vega-decay]]
- See also: [[concepts/09-risk-measurement-ii/higher-order-sensitivities-and-their-names]], [[glossary]], [[formulas]]
