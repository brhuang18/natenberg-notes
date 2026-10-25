# Expected value, edge and theoretical value

**One-line definition:** the *expected value* is the average payout you would get over very many repetitions; the *theoretical value* is the price at which you would just break even in the long run, which is the expected value brought back to today's money.

## Intuition
Think of a casino. It does not know whether any single spin will win or lose. It knows that, over thousands of spins, the average result is very predictable. It sells each bet for slightly more than the average payout, and that gap is its profit.

An option trader does the same: work out the *average* payoff, compare it with the market price, and trade when the price is on the right side.

## The maths
**Expected value.** If outcomes $x_1, x_2, \dots, x_n$ happen with probabilities $p_1, \dots, p_n$ (adding up to 1):

$$E = p_1 x_1 + p_2 x_2 + \dots + p_n x_n = \sum_{i=1}^{n} p_i\, x_i$$

- $x_i$ = the $i$-th possible payout
- $p_i$ = the chance of it, as a decimal (20% is $0.20$)
- $\sum$ means "add up the following for $i = 1$ to $n$" ([[00-maths-refresher/summation-notation]])

So the expected value is a **weighted average**: likely outcomes count more.

**Theoretical value.** If the payout arrives later, today's value is smaller, because you could have earned interest on the money. Divide by the growth factor:

$$\text{theoretical value} = \frac{E}{1 + r\,t}$$

- $r$ = interest rate per year (as a decimal)
- $t$ = time until the payout, in years (2 months is $2/12$)
- Why divide: a sum of money $V$ today grows to $V(1 + rt)$ later. We want the $V$ that grows to $E$, so $V = E/(1 + rt)$. See [[00-maths-refresher/present-value-and-discounting]].

**Edge.** The difference between the expected value (or theoretical value) and the price actually charged:

$$\text{edge} = \text{price} - \text{theoretical value} \quad(\text{for the seller; negative for the buyer})$$

## Worked examples (the book's)
**1. The die.** You are paid the number that comes up.

$$E = \frac{1 + 2 + 3 + 4 + 5 + 6}{6} = \frac{21}{6} = 3.5$$

- Pay less than 3.50 per roll: you win in the long run. Pay more: you lose. Pay exactly 3.50: you break even.
- On any single roll you can never receive exactly 3.50. The 3.50 only shows up as an *average over many rolls*.

**2. Roulette (38 slots: 1 to 36, 0 and 00).** Pick one number; if it comes up you get 36, otherwise 0.

$$E = \frac{1}{38} \times 36 + \frac{37}{38} \times 0 = \frac{36}{38} = 0.9474$$

- The casino sells this bet for 1.00. Edge $= 1.00 - 0.9474 \approx 0.05$, about 5 cents per dollar bet.
- If you could instead buy the bet for 0.88 you would have an edge of $0.9474 - 0.88 \approx 0.07$. (The book rounds the expected value to 95 cents and says 7 cents.)

**3. Roulette with delayed winnings.** The casino pays the winnings in two months. Interest is 12% a year.

1. $r = 0.12$, $t = 2/12$, so $rt = 0.02$ and the growth factor is $1.02$.
2. Theoretical value $= 0.95 / 1.02 = 0.9314 \approx 0.93$ (using the book's rounded 0.95).
3. Check the logic: if you pay 0.95 today you lose the interest your 0.95 would have earned in the bank, about 2 cents. The fair price is lower by that amount.

**4. Extra benefits (like dividends).** If the casino also sends a 1-cent bonus a month from now, add it: $0.93 + 0.01 = 0.94$. Dividends play the same role for stocks.

## The long run is not guaranteed: risk
A 5% edge only pays off if you survive long enough. The book's point: a player could win several spins in a row, and a casino without enough capital could go out of business before the average has time to work.

For an option trader the lesson is that **managing risk is at least as important as calculating the theoretical value**. The model gives an expected value; reality hands out one outcome at a time.

## Common confusions
- **"Expected" does not mean "likely".** The die's expected value is 3.5, a result that cannot happen. It is an average, not a prediction.
- **Edge needs repetition.** One trade with a positive edge can still lose money.
- **Theoretical value is not market price.** The market may price an option above or below its theoretical value. Spotting the difference is the whole game.

## Related
- Chapter: [[chapters/05-theoretical-pricing-models]]
- Maths needed: [[00-maths-refresher/probability-and-expected-value]], [[00-maths-refresher/present-value-and-discounting]], [[00-maths-refresher/summation-notation]]
- Previous: [[concepts/05-theoretical-pricing-models/direction-and-speed]]
- Next: [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]]
- See also: [[glossary]], [[formulas]]
