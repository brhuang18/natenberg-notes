# Executing a spread: leg risk, the spread's own market, and why only the total matters

**One-line definition:** executing a spread means getting all its legs done at prices that add up to the spread price you want; the risk of getting only some legs filled is **leg risk** (execution risk), and the cure is to trade the spread as one package when you can.

## Intuition
A spread is only a spread once *all* its legs are on. If you have done only the first leg, you are not hedged: you are just holding a naked position until you finish. So the question "how do I get in?" matters almost as much as "what do I want?"

## The ideas, step by step
**1. Doing it one leg at a time (leg risk).** In some markets no one will quote the whole spread, so you trade each leg separately. Between the first and last leg you are exposed. The book's rule of thumb: **do the hardest leg first.**
- Some legs are harder to execute because of the liquidity in their markets.
- If you do the hard leg first and succeed, the easy legs are easy to complete, so execution risk is small.
- If you do the easy leg first and then cannot do the hard leg at a reasonable price or in time, you are stuck with a **naked position**.

**2. The spread as one contract.** In many markets spreads trade as a single instrument with one bid and one offer, however complex. You get it from the quotes of the legs (page 164).

Contract A is bought, contracts B and C are sold:

| Contract | Bid | Ask |
|---|---|---|
| A | 128 | 131 |
| B | 47 | 49 |
| C | 68 | 70 |

- To **sell the spread** (sell A, buy B, buy C): you sell A at its bid, buy B and C at their asks:

$$128 - 49 - 70 = 9$$

- To **buy the spread** (buy A, sell B, sell C): you buy A at its ask, sell B and C at their bids:

$$131 - 47 - 68 = 16$$

So the spread's market is **9 bid, 16 offer**, a width of 7. That 7 is the sum of the three individual widths ($3 + 2 + 2$).

**3. Asking for a market on the whole spread.** A market maker who does all three legs at once takes less risk than one who does them separately, so he will usually quote a *tighter* market, perhaps **11 bid, 14 offer** (width 3). Trading it as one transaction is better than three separate trades, for the trader who buys at 14 instead of 16, or sells at 11 instead of 9.

**4. Reporting the leg prices.** Even when a spread is done as one trade, many exchanges require the individual contract prices to be reported. But only the **total** matters to the two parties. Buying the spread at 14:

$$129 - 47 - 68 = 14 \qquad 131 - 48 - 69 = 14 \qquad 200 - 86 - 100 = 14$$

All three are the same trade. (In practice exchanges prefer leg prices near the current market, otherwise it may look like someone is doing something unethical or illegal, so 200, 86 and 100 would not be accepted.)

## Worked example: choosing a price
You want to buy the spread. The market of the legs gives 16, the spread market maker says 11/14. You pay 14. Compare:

| Method | Price paid | Saving vs legs |
|---|---|---|
| Three separate trades at the ask/bid | 16 | - |
| One spread trade at the offer | 14 | 2 |

If you tried to sell instead: legs give 9, the spread market gives 11, so the spread trade is better by 2 again.

## Common confusions
- **Why does buying the spread use the ask on A but the bid on B and C?** You buy what you buy at the ask and sell what you sell at the bid. Each leg is crossed the "bad" way, so the spread's bid-ask is wider than any single leg's.
- **The spread price can be negative or any size.** Only the signed sum matters ([[00-maths-refresher/ratios-and-32nds]]).
- **Doing the hard leg first is about risk, not price.** You may still pay up for it, but the alternative (being stuck with a naked easy leg) is worse.
- **Leg prices that add up are not always acceptable.** The exchange can object to unrealistic leg prices.

## Related
- Chapter: [[chapters/10-introduction-to-spreading]]
- Previous: [[concepts/10-introduction-to-spreading/intermarket-and-ratio-spreads]]
- Next: [[concepts/10-introduction-to-spreading/option-spreads-delta-gamma-vega-rho]]
- Maths needed: [[00-maths-refresher/ratios-and-32nds]], [[00-maths-refresher/signs-and-running-totals]]
- See also: [[glossary]], [[formulas]]
