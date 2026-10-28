# Signs and running totals

**One-line summary:** hedging arithmetic is mostly keeping track of plus and minus signs (bought or sold, long or short, cash in or cash out) and adding up a running total week after week.

Used in: [[concepts/08-dynamic-hedging/delta-neutral-adjustments]], [[concepts/08-dynamic-hedging/stock-option-hedge-walkthrough]], [[concepts/08-dynamic-hedging/futures-option-hedge-and-variation]], [[chapters/08-dynamic-hedging]]

## Intuition
There are two different kinds of plus and minus, and mixing them up is the commonest slip (the book itself prints a few):

1. **What you hold:** long (own it) is $+$, short (owe it) is $-$.
2. **What happens to your cash:** money in is $+$, money out is $-$.

Buying and selling flip *both* in opposite directions:

| Action | Position change | Cash |
|---|---|---|
| **Buy** 4 contracts at 99.50 | $+4$ contracts | $-398.00$ (cash goes out) |
| **Sell** 4 contracts at 99.50 | $-4$ contracts | $+398.00$ (cash comes in) |

So when you sell, your *position* goes down and your *cash* goes up. It feels odd at first, but it is the only way the books balance.

## The maths
**Delta signs.** Each option or underlying has a delta; multiply by how many you hold ($+$ long, $-$ short):

| Holding | Delta per unit | Total delta contribution |
|---|---|---|
| Long 100 calls, delta 54 | $+54$ | $+100 \times 54 = +5{,}400$ |
| Short 54 underlying contracts | $+100$ | $-54 \times 100 = -5{,}400$ |
| Short 100 puts, delta $-35$ | $-35$ | $-100 \times (-35) = +3{,}500$ |

Notice the last row: a **negative** quantity times a **negative** delta gives a **positive** result, so a short put has positive delta (it gains when the underlying rises). That is why you offset it by *selling* the underlying. ([[concepts/07-risk-measurement-i/risk-measures-of-the-underlying-and-signs]])

**Total delta position:**

$$\text{total delta} = \sum (\text{quantity} \times \Delta)$$

**The rule for an adjustment.** The trade has the *opposite* sign of the imbalance. A total delta of $+400$ means you have too much positive delta, so you sell; $-1{,}900$ means too little, so you buy.

$$\text{contracts to sell} = \frac{\text{total delta}}{100} \qquad (\text{negative result} = \text{buy})$$

**Running totals.** Keep one running number for the position and update it with every trade. Writing short as a negative number, the example from Chapter 8 is:

| Event | Change in position | Running position |
|---|---|---|
| Original hedge: sell 50 | $-50$ | $-50$ |
| Week 1: sell 4 | $-4$ | $-54$ |
| Week 2: buy 19 | $+19$ | $-35$ |
| Week 3: sell 8 | $-8$ | $-43$ |

Check after each step: $100 \times \Delta_{\text{call}} + 100 \times (\text{running position}) = 0$. Week 3: $100 \times 43 + 100 \times (-43) = 0$.

**Interest on a cash flow.** Interest has the *same sign* as the cash flow: a credit (positive) earns interest and a debit (negative) costs interest. ([[00-maths-refresher/simple-interest-and-time-fractions]])

$$\text{interest} = \text{cash} \times r \times \frac{\text{days left}}{365}$$

Week 1: $+398.00 \times 0.06 \times 63/365 = +4.12$. Week 2: $-1{,}762.25 \times 0.06 \times 56/365 = -16.22$.

**Adding a whole column.** The capital sigma (Σ) just means "add them all up" ([[00-maths-refresher/summation-notation]]):

$$\sum \text{cash flows} = 398.00 - 1{,}762.25 + 766.80 + \dots = \text{total}$$

## Worked example
You are short 35 futures and the price rises from 60.83 to 62.78. Does cash go in or out?

- Short means a negative position, $-35$. The price change is $+1.95$.
- Variation = position $\times$ price change $= (-35) \times (+1.95) = -68.25$. Cash goes **out**.

The book's formula for a short position, $\text{number short} \times (\text{old price} - \text{new price}) = 35 \times (60.83 - 62.78) = -68.25$, is the same thing written so that the number short is positive.

## Common confusions
- **Is "short 54" a negative number?** In the position column we write $-54$; in the book's tables it is written "Short 54" with the sign carried by the word. Be consistent: if you write it as $-54$, then the delta of that position is $-54 \times 100$.
- **Check your signs by the sanity test.** After every adjustment the total delta must be zero. If it is not, a sign went wrong.
- **The book's own tables have sign slips.** For example Figure 8-4 prints a total delta of $-3{,}000$ in week 9 next to "Sell 30". Rule: positive total means sell, so it should read $+3{,}000$. ([[chapters/08-dynamic-hedging]])

## Related
- Chapter: [[chapters/08-dynamic-hedging]]
- See also: [[00-maths-refresher/README|Maths refresher]], [[glossary]]
