# Option replication: the principle behind the hedge

**One-line definition:** a dynamic hedging process replicates an option position; the cost of replication is the sum of all the hedge's cash flows, and the present value of that sum equals the option's theoretical value.

## Intuition
When we bought the call at 5.00 and hedged it, we were doing two things at once. We **owned** a real call. And through the hedge (short the stock, adjust every week) we were *manufacturing* the opposite of that call: a synthetic short call. Holding the real call and the synthetic short call together, the market direction and the option itself net out, and what is left is the difference between what we paid for the real one (5.00) and what it costs to manufacture the synthetic one (5.89). The 0.89 is our profit.

The book's way to say it: in a sense, dynamic hedging let us "take the other side of the trade, but at the option's true theoretical value". When we bought calls, we sold the same calls at theoretical value through the hedge. When we sold puts, we bought the same puts at theoretical value through the hedge.

## The principle
The book states it in one sentence: in theory we can replicate an option position through a dynamic hedging process. The cost of replication is the sum of the cash flows of the hedging process, and the present value of that sum equals the option's theoretical value.

$$\text{theoretical value} = \text{present value of the sum of all cash flows from the dynamic hedge}$$

## Checking it with the book's numbers
**Stock example.** The total profit today was $+89.21$. That included the 500 we paid for the calls. Remove it:

$$\text{PV of the hedge's cash flows} = 89.21 + 500.00 = 589.21 \approx 100 \times 5.89 = 589.00$$

The hedge (the stock sale, the weekly adjustments, the final buy-back, the option's closing value, and all the interest) produced about 589 today: the theoretical value of 100 calls.

**Futures example.** The total profit today was $+23.96$, and it included the 170 we received for the puts. Remove it:

$$\text{PV of the hedge's cash flows} = 23.96 - 170.00 = -146.04 \approx -100 \times 1.46 = -146.00$$

The hedge cost about 146 today to "buy back" the 100 puts at their theoretical value. We received 170 and paid 146: profit 24.

## Why this matters
- **It explains why the model's value is the right price to hedge against.** If you can build the option from the underlying at a cost equal to the model value, then buying the option for less (or selling for more) is a genuine, capturable edge: you can lock the difference in by running the replication on the other side.
- **It makes it possible to create an option that does not exist.** Chapter 17's portfolio insurance does exactly this: someone holding stock who cannot find a put can create the equivalent call by selling off part of the holding according to a delta from the model. For example, with a call delta of 75, hold 75% of the original shares (sell 250 of 1,000); when delta falls to 60, hold 600. This is a preview, to be covered when we get to Chapter 17.
- **It links to the next chapters.** The sum of "unhedged amounts" in [[concepts/08-dynamic-hedging/gamma-and-the-unhedged-amount]] is the replicating cost accumulating; the proof that, with continuous rehedging, it equals the Black-Scholes value is the subject of later chapters.

## Limits
The replication is exact only if all the model assumptions hold: you can rehedge continuously, volatility and interest are constant, and the market is frictionless ([[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]]). In practice "continuous rehedging is not possible in the real world. Nor are all the model assumptions entirely accurate", but traders have found "using a dynamic hedging strategy, even if only at discrete intervals, is the best way to capture the difference between an option's price and its theoretical value." Chapter 23 revisits these assumptions.

## Common confusions
- **Replication is not a guarantee.** On a single path the result will be off by some amount; our simulation shows typical scatter of tens against a prediction of 89 ([[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]]).
- **The hedger need not hold to expiration to benefit.** If the market's implied volatility moves to match the model's value, the real option's price rises to the replication cost and the profit can be taken at once. [[concepts/08-dynamic-hedging/implied-volatility-moves-and-holding-the-hedge]]
- **"Cost of replication" can be negative or positive.** For a long call you *receive* cash from the hedge (selling stock) and so the PV sum is positive 589; for a short put the hedge costs money, so the PV sum is negative 146. The sign tells you which side of the replication you are on.

## Related
- Chapter: [[chapters/08-dynamic-hedging]]
- Previous: [[concepts/08-dynamic-hedging/futures-option-hedge-and-variation]]
- Earlier: [[concepts/05-theoretical-pricing-models/riskless-hedge-and-hedge-ratio]], [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]
- Later: Chapter 17 (hedging with options, portfolio insurance), Chapters 18-19 (Black-Scholes and binomial pricing)
- Maths needed: [[00-maths-refresher/present-value-and-discounting]]
- See also: [[glossary]], [[formulas]]
