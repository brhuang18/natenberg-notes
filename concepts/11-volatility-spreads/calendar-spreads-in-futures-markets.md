# Calendar spreads in futures markets (different underlyings)

**One-line definition:** in a stock-option calendar spread both options share one underlying (the stock), but in a futures-option calendar spread the two options can sit on **different futures contracts**, so you may also need a **futures spread** to hedge the gap between the futures.

## Intuition
For General Electric stock, a March option and a June option both depend on **one** price: the GE share price. It cannot be two prices at once.

For a futures option, the underlying is a *specific futures contract*. A March option is on the March future. A June option is on the June future. March and June futures normally move together, but nothing forces them to: short-term supply and demand (especially in commodities) can push one up while the other stays still. So a March/June calendar spread has an **extra hidden risk**: the March future could rise relative to the June future. This is the same idea as the futures calendar spread in Chapter 10, now sitting underneath an option spread ([[concepts/10-introduction-to-spreading/cash-and-carry-and-calendar-spreads]]).

When both options use the *same* future (for example an April option and a June option, if monthly options exist and both settle into the June future), the problem does not arise.

## The hedge
You buy a March/June call calendar spread: **buy 10 June calls, sell 10 March calls**, both at the money (delta about 50).

| Leg | Delta position |
|---|---|
| $+10$ June calls | $+10 \times 50 = +500$ |
| $-10$ March calls | $-10 \times 50 = -500$ |

The total delta is zero, but it is hiding two separate exposures: $+500$ to the June future and $-500$ to the March future. If March moves relative to June you can still lose. To remove it, hedge each month with its own future (one future = 100 deltas):

- Sell $500/100 = 5$ **June futures** (offsets the June $+500$).
- Buy $500/100 = 5$ **March futures** (offsets the March $-500$).

The complete position (deltas in brackets):

$$+10 \text{ June calls } (+500),\; -5 \text{ June futures } (-500),\quad -10 \text{ March calls } (-500),\; +5 \text{ March futures } (+500)$$

You are now sensitive only to volatility (and time), not to a change in the March/June futures gap.

## Common confusions
- **"This is not needed for stock options."** Correct: for stock options the underlying is the same for all months. The balancing is not necessary, and not even possible.
- **The futures hedge here is itself a futures calendar spread** (buy March, sell June, as in Chapter 10). In Chapter 10 such a spread was a bet on the gap between months; here it is only a hedge, so the option calendar is not hurt by that gap.
- **You hedge deltas, not contracts.** If the options had a delta of 40 you would need $400/100 = 4$ futures spreads.
- **Interest rates matter little for futures options** (no carrying cost) but they can affect the relative value of different futures months; the book says that risk is offset by this same futures spread (footnote 8, page 194).

## Related
- Chapter: [[chapters/11-volatility-spreads]]
- Previous: [[concepts/11-volatility-spreads/calendar-spreads-volatility-and-opposite-wishes]]
- Next: [[concepts/11-volatility-spreads/time-butterflies]]
- Earlier: [[concepts/10-introduction-to-spreading/cash-and-carry-and-calendar-spreads]], [[concepts/08-dynamic-hedging/futures-option-hedge-and-variation]]
- Maths needed: [[00-maths-refresher/signs-and-running-totals]]
- See also: [[glossary]], [[formulas]]
