# Series of bets and dynamic hedging

**One-line definition:** dynamic hedging means holding a delta-neutral position in the underlying against an option and re-balancing it over the option's whole life, so that one big bet on the option's mispricing becomes many small bets, each at the same favourable odds.

## Intuition
Imagine a casino game where you win 51% of the time. If you play one hand, you lose almost half the time. If you play 10,000 hands, you almost surely finish ahead, and the result is close to what the odds predict. The edge never changed; you simply gave luck many chances to average out.

A theoretical pricing model gives you an edge in the same way. If you buy a call for 5.00 that the model says is worth 5.89, the *average* result over many such trades is a profit of 0.89 per option. But a single trade is one hand: the stock can rise or fall and you could lose.

The book's idea is that you do not have to accept one hand. By hedging the option against the underlying and re-balancing regularly, you break the option's life into a string of short periods. Each period is "one bet", and each new period starts with a fresh delta-neutral position, so each bet depends only on **how much** the market moves (volatility), not on **which way**.

## The maths
There is not much formula to fear here, only one idea about cancelling.

**Step 1: why a delta hedge cancels direction.** Delta is the slope of the option's value against the underlying ([[concepts/07-risk-measurement-i/delta]]). For a small move $\Delta S$ in the underlying:

$$\text{change in option value} \approx \Delta \times \Delta S$$

If you are long one option and short $\Delta$ of the underlying (as a decimal), the short stock changes by $-\Delta \times \Delta S$. Add the two:

$$\Delta \times \Delta S - \Delta \times \Delta S = 0$$

So for small moves the position does not care about direction. In contracts, with whole-number deltas:

$$\text{underlying contracts to sell} = \frac{\text{number of options} \times \Delta}{100}$$

**Step 2: why this has to be repeated.** The slope changes as the price and time change (that is gamma, [[concepts/07-risk-measurement-i/gamma]]). After a bigger move the old hedge is no longer neutral, so we recompute delta and trade the underlying again. The extra trade is called an **adjustment**. See [[concepts/08-dynamic-hedging/delta-neutral-adjustments]].

**Step 3: static vs dynamic.** A **static hedge** is put on once and held to a fixed maturity (the protective strategies of Chapter 17). A **dynamic hedge** is re-balanced for the whole life of the option. The model's edge is only reliably captured by the dynamic version.

## Worked example
Stock 97.70, June 100 call with theoretical value 5.89 and offer price 5.00 (underpriced by 0.89), delta 50. Buy 100 calls and sell 50 underlying contracts.

| Position | Contracts | Delta | Delta position |
|---|---|---|---|
| Long June 100 calls | 100 | 50 | $+5{,}000$ |
| Short underlying | 50 | 100 | $-5{,}000$ |
| **Total** | | | **0** |

One week later the stock is 99.50 and the delta is 54: the calls are now $+5{,}400$ and the underlying still $-5{,}000$, so the position is $+400$. "We can think of this as the end of one bet, with another bet about to begin." Sell 4 contracts to get back to $-5{,}400$, and the next bet starts neutral. Full table: [[concepts/08-dynamic-hedging/stock-option-hedge-walkthrough]].

## Common confusions
- **"A hedged position is riskless."** It is neutral to *direction* (for small moves) but not to volatility. If the stock barely moves, the hedge loses the option's time value, so it still has a result that depends on realized volatility. [[concepts/08-dynamic-hedging/realized-volatility-and-the-race]]
- **"Rehedging gives me more expected profit."** No. Adjustments do not change the expected return; they only reduce the effects of good and bad luck. [[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]]
- **"The model guarantees 89."** It predicts an average. The book says the example was "carefully constructed" so the actual result is close; real results typically scatter around the prediction.
- **Why use the underlying to adjust?** An underlying contract has delta 100 and no theoretical value, so trading it changes delta without changing the theoretical edge.

## Related
- Chapter: [[chapters/08-dynamic-hedging]]
- Earlier: [[concepts/05-theoretical-pricing-models/riskless-hedge-and-hedge-ratio]], [[concepts/07-risk-measurement-i/delta]]
- Next: [[concepts/08-dynamic-hedging/delta-neutral-adjustments]]
- Maths needed: [[00-maths-refresher/signs-and-running-totals]]
- See also: [[glossary]], [[formulas]]
