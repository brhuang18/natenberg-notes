# Implied values

**One-line definition:** if you believe a contract's price is fair, you can rearrange the pricing formula to solve for any *missing* input. The answer is the **implied value** of that input: what the market must be assuming.

## Intuition
A pricing formula takes inputs and produces a price. Run it backwards: *given* the price, what inputs would justify it?

Think of a restaurant bill. If you know the total, the number of diners and the tip, you can work out the average meal price. The market gives you the total (the forward price); you recover whichever ingredient you do not know.

This idea comes back again and again in the book. Later it becomes **implied volatility**, the most important implied value in options.

## The maths
Start with the stock forward formula from [[concepts/02-forward-pricing/forward-price-by-instrument]]:

$$F = S \times (1 + r t) - D$$

Rearrange it for each unknown in turn (the algebra is shown step by step in [[00-maths-refresher/rearranging-formulas]]):

| Solve for | Formula |
|---|---|
| Implied spot price | $S = \dfrac{F + D}{1 + r t}$ |
| Implied interest rate | $r = \dfrac{\dfrac{F + D}{S} - 1}{t}$ |
| Implied dividend | $D = S \times (1 + r t) - F$ |

## Worked example (the book's numbers)
Stock $S = 67.00$, $t = 8/12$, $r = 6\%$, $D = 0.66$, and the market price of the 8-month forward is $F = 69.50$ (fair value was 69.02). Which input might be "wrong"?

**Implied interest rate** (assume everything else is right):

1. $(F + D)/S = (69.50 + 0.66) / 67.00 = 70.16 / 67.00 = 1.04716$
2. Subtract 1: $0.04716$
3. Divide by $t = 8/12$: $0.04716 / 0.6667 = 0.0707$

So the market is behaving as if the interest rate were **7.07%**, not 6%.

**Implied dividend** (assume everything else is right):

$$D = 67.00 \times (1 + 0.06 \times 8/12) - 69.50 = 69.68 - 69.50 = 0.18$$

The market is behaving as if only \$0.18 of dividends will be paid, not \$0.66. If two payments are expected, that is about \$0.09 each.

**Implied spot price** (our own extra example): $S = (69.50 + 0.66)/1.04 = 67.46$. The forward price of 69.50 is consistent with a stock price of about 67.46, not 67.00.

## Common confusions
- Only **one** thing can be solved for at a time. You must hold all the other inputs fixed. So "implied rate = 7.07%" assumes the dividend of 0.66 is right.
- An implied value is not a fact. It is "the market's consensus *if* my other assumptions are right". It might signal a mistake in your inputs rather than a mistake by the market.

## Related
- Chapter: [[chapters/02-forward-pricing]]
- Maths needed: [[00-maths-refresher/rearranging-formulas]]
- See also: [[concepts/02-forward-pricing/arbitrage-and-cash-and-carry]], [[glossary]], [[formulas]]
