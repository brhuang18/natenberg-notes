# Probability and expected value (weighted averages)

**One-line summary:** a probability is a number between 0 and 1 saying how likely something is; an expected value is the average outcome, where likelier outcomes count for more.

Used in: [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]], [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]], [[chapters/05-theoretical-pricing-models]]

## Intuition
If you roll a fair die many times, each face comes up about one time in six. A probability of $1/6$ means "about 1 in every 6 tries, in the long run". An expected value asks: if I repeated this over and over, what would the *average* result be?

## The maths
**Probabilities** are written as decimals or percentages: $20\% = 0.20 = 1/5$. Rules:
- Each probability is between 0 and 1.
- The probabilities of all possible outcomes add up to exactly 1 (100%).

**Expected value.** For outcomes $x_1, \dots, x_n$ with probabilities $p_1, \dots, p_n$:

$$E = p_1 x_1 + p_2 x_2 + \dots + p_n x_n = \sum_{i=1}^{n} p_i\, x_i$$

The $\sum$ ("sigma") is just shorthand for "add them all up" ([[00-maths-refresher/summation-notation]]).

**Equal chances is the ordinary average.** If every outcome has the same probability $1/n$:

$$E = \frac{1}{n}(x_1 + \dots + x_n)$$

so a die gives $(1 + 2 + 3 + 4 + 5 + 6)/6 = 3.5$.

**Why it is called a weighted average.** Each outcome is multiplied by a weight (its probability). Heavier weights pull the average towards that outcome.

## Worked example
Five stock prices at expiration with unequal chances:

| Price $x_i$ | Probability $p_i$ | $p_i \times x_i$ |
|---|---|---|
| 80 | 0.10 | 8.0 |
| 90 | 0.20 | 18.0 |
| 100 | 0.40 | 40.0 |
| 110 | 0.20 | 22.0 |
| 120 | 0.10 | 12.0 |
| **Total** | **1.00** | **100.0** |

1. Check the probabilities add to 1: $0.10 + 0.20 + 0.40 + 0.20 + 0.10 = 1.00$.
2. Multiply each price by its probability (right column).
3. Add: $8 + 18 + 40 + 22 + 12 = 100$. The expected price is 100.

The same approach works for *option payoffs* instead of prices: multiply the payoff at each price by that price's probability and add.

## Common confusions
- **Expected does not mean "will happen".** The die's expected value 3.5 is not a possible roll.
- **Probabilities must add to 1.** If your table adds to 0.9 or 1.1, something is wrong.
- **Averages are about the long run.** A single outcome can differ a lot from the expected value.

## Related
- Index: [[00-maths-refresher/README|Maths refresher]]
