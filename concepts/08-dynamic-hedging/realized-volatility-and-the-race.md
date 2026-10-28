# Realized volatility and the race

**One-line definition:** a hedged option position is a race between the **time value the option loses** and the **cash the adjustments earn**; the realized volatility of the underlying sets the pace of the adjustments, and the volatility at which the race ends in a tie is the option's implied volatility at the price we paid.

## Intuition
Think of the hedge as two runners. One runner, **time decay**, steadily takes value out of the option we bought. The other, the **adjustments**, collect small profits every time the stock moves. If the stock is jumpy, the adjustments are frequent and large, and they win. If the stock is calm, there is little to collect and time decay wins. The model is the referee: if we bought the option for less than its theoretical value, the adjustments will win (on average); if more, time decay wins.

The pace is set by **realized volatility** of the underlying: bigger and more frequent moves mean more and larger adjustments. And since the *price we paid* sets how much time decay we must beat, the volatility at which the two runners tie is exactly the option's **implied volatility at that price**.

## The maths
Suppose volatility turns out to be higher or lower than our 37.62% forecast:

- **Higher:** greater price fluctuations, more and larger adjustments, more profit. This agrees with the principle that higher volatility increases option values ([[concepts/06-volatility/volatility-and-option-values]]).
- **Lower:** fewer and smaller adjustments, less profit.
- **Low enough:** the adjustment profit just offsets the other components and the hedge's profit is exactly zero. This breakeven volatility is the implied volatility of the option at the price we paid.

In the example, the implied volatility of the June 100 call at 5.00 is **32.40%**, found by asking the model: what volatility makes the call worth 5.00? ([[concepts/06-volatility/implied-volatility]]) So:

$$\text{realized volatility} > 32.40\% \Rightarrow \text{profit}, \qquad \text{realized volatility} < 32.40\% \Rightarrow \text{loss}$$

**Why "squared" moves matter (our extension).** From Chapter 6, over a short time $dt$ the typical squared price move is about $S^2\sigma^2\,dt$ ([[concepts/06-volatility/scaling-volatility-for-time]]). From [[concepts/08-dynamic-hedging/gamma-and-the-unhedged-amount]] each interval earns roughly $\tfrac12\Gamma(\Delta S)^2 + \Theta\,dt$. When the realized $(\Delta S)^2$ matches the amount the option price already assumes, gamma gain equals theta loss; any more movement is profit, any less is loss. That is the race in one line. (The exact statement is the Black-Scholes equation pointed to in [[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]].)

## Worked example
Our simulation of the book's hedge: 10,000 paths with daily rehedging, deltas always computed with the 37.62% forecast, but the stock actually moves with the "true" volatility in the first column.

| True volatility | Average profit (per 100 options) |
|---|---|
| 20% | $-212$ |
| 25% | $-127$ |
| 30% | $-41$ |
| 32.4% | $0$ |
| 35% | $+44$ |
| 37.62% | $+89$ |
| 45% | $+216$ |
| 50% | $+302$ |

The points sit almost exactly on a line: the theoretical value of the call at the true volatility, minus the 5.00 paid, times 100. Check at 37.62%: value 5.89, so $100 \times (5.89 - 5.00) = 89$. Check at 32.4%: value 5.00, so profit 0.

![Average hedge profit against true volatility](../../images/ch08-hedge-pnl-vs-volatility.png)

Notice what is **not** on the horizontal axis: where the stock ends up. We trade only the underlying after the first day and never touch the options; the result depends on realized volatility, not direction.

## Common confusions
- **We never know the true volatility.** The book's "crystal ball" is a device to show how the machinery works. In practice 37.62% is a forecast; if it is wrong, the profit is whatever the *actual* volatility gives.
- **Why 37.62% in the deltas, if the real volatility is different?** The model assumes volatility is constant, so the hedge keeps using the same number. Our simulation does the same.
- **Breakeven volatility again.** This is the same idea as the breakeven volatility of a position in Chapter 7 ([[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]]): the volatility at which our theoretical profit is zero.
- **Higher volatility is better only if you are long options.** For a hedger who *sold* the options (the put in the futures example), higher realized volatility means more adjustments that lose. [[concepts/08-dynamic-hedging/futures-option-hedge-and-variation]]

## Related
- Chapter: [[chapters/08-dynamic-hedging]]
- Previous: [[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]]
- Next: [[concepts/08-dynamic-hedging/implied-volatility-moves-and-holding-the-hedge]]
- Earlier: [[concepts/06-volatility/realized-volatility]], [[concepts/06-volatility/implied-volatility]]
- Maths needed: [[00-maths-refresher/standard-deviation-and-variance]]
- Code: [[code/dynamic_hedging.ipynb]]
- See also: [[glossary]], [[formulas]]
