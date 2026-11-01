# What is a spread?

**One-line definition:** a **spread** is a strategy that takes opposing positions in different but related instruments, so that when conditions change one position tends to gain while the other tends to lose.

## Intuition
Picture two people on a seesaw. If both move the same amount, the seesaw never tilts. A spread is the same: you hold two things that react to the market in opposite ways. If they react by exactly the same amount, the spread's value never changes and there is nothing to earn. The strategy only makes sense when you believe the two will change at **different rates**, so the *gap* between them moves in your favour.

That is the key shift in thinking. A directional trader asks "will the price go up?" A spread trader asks "will the **relationship** between these two prices change?" The overall level of the market matters much less.

## The ideas, step by step
**1. Why not just trade direction?** The chapter opens with other trading styles:
- **Scalping** (quote a bid and an offer around an equilibrium price, trade often, keep a tiny profit each time, never hold a position long). It needs a very liquid market; option markets are rarely liquid enough.
- **Directional trading** (bet on up or down). In *options* this is awkward: even when the underlying moves the way you wanted, volatility changes and the passage of time can also move the option price, so you can be right on direction and still lose. If direction is all you care about, trade the underlying: if you are right you are sure to profit.
- **Spreading.** Most successful option traders do this.

**2. Why option traders must spread.** An option's theoretical value comes from the laws of probability, and those only "even out over long periods". So an option trader has to hold positions for a long time while the market catches up to theoretical value, and during that time all sorts of changes (price, volatility, time) can threaten the position. Spreading reduces the effect of short-term bad luck while keeping the theoretical edge. [[concepts/10-introduction-to-spreading/casino-spreading-and-short-term-bad-luck]]

**3. Vocabulary.**
- **Leg** - one position within the spread (long 1 call, short 1 future, and so on). A spread has two or more legs.
- **Buy the spread / sell the spread** - the spread has a price (the signed sum of its legs, [[00-maths-refresher/ratios-and-32nds]]). Following the book's crack-spread wording, you *buy* the spread when you buy the side that is worth more and sell the other (buy the products, sell crude), and you *sell* it when you do the reverse.
- **Intramarket spread** - all legs on the same underlying (cash vs forward, near month vs far month). [[concepts/10-introduction-to-spreading/cash-and-carry-and-calendar-spreads]]
- **Intermarket spread** - legs in different markets (gold vs silver, S&P 500 vs Dow). [[concepts/10-introduction-to-spreading/intermarket-and-ratio-spreads]]
- **Arbitrage spread** - a spread based on an exact pricing relationship, buying and selling the same or very closely related things to profit from a mispricing. [[concepts/02-forward-pricing/arbitrage-and-cash-and-carry]]

## Worked example (ours, to show "different rates")
Long 1 contract of A at 100, short 1 contract of B at 90. The spread $A - B = 10$.

| Event | A | B | Spread $A-B$ | Your P&L |
|---|---|---|---|---|
| Start | 100 | 90 | 10 | 0 |
| Market rises, both +5 | 105 | 95 | 10 | $+5 - 5 = 0$ |
| Market rises, A +6, B +4 | 106 | 94 | 12 | $+6 - 4 = +2$ |
| Market falls, A -3, B -5 | 97 | 85 | 12 | $-3 + 5 = +2$ |

The market's direction does not matter. What matters is whether A moves more than B.

## Common confusions
- **A spread is not always "risk-free".** It removes *some* risks (usually direction) and leaves others (changes in interest rates, storage costs, the relationship itself failing). [[concepts/10-introduction-to-spreading/cash-and-carry-and-calendar-spreads]]
- **A spread does not need to be two legs.** The crack spread has three; option spreads can have many.
- **"Opposing" does not mean "equal".** Many spreads use unequal numbers (3 A against 1 B). The legs are balanced by *value* or by *risk*, not by count. [[concepts/10-introduction-to-spreading/intermarket-and-ratio-spreads]]

## Related
- Chapter: [[chapters/10-introduction-to-spreading]]
- Next: [[concepts/10-introduction-to-spreading/cash-and-carry-and-calendar-spreads]]
- Earlier: [[concepts/08-dynamic-hedging/series-of-bets-and-dynamic-hedging]], [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]
- Maths needed: [[00-maths-refresher/ratios-and-32nds]]
- See also: [[glossary]], [[formulas]]
