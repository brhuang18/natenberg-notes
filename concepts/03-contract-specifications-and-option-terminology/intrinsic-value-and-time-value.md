# Intrinsic value and time value

**One-line definition:** an option's price (its **premium**) is always made of two parts: **intrinsic value** (what you would gain by exercising right now) plus **time value** (everything else people are willing to pay).

## Intuition
- **Intrinsic value** is the "buy low, sell high" profit you could lock in this instant. A call lets you buy at the exercise price $X$; if the market price $S$ is higher, you can buy at $X$ and sell at $S$ and keep the difference. If $S$ is below $X$, there is nothing to gain, so intrinsic value is zero (not negative).
- **Time value** (also called *time premium* or *extrinsic value*) is the extra on top. People pay it mainly for the **protection** an option gives compared with simply holding the underlying: you keep the upside but your loss is limited.

## The maths
With $S$ = underlying price and $X$ = exercise price (the $\max$ function is explained in [[00-maths-refresher/max-function]]):

$$\text{call intrinsic value} = \max(0,\; S - X) \qquad\qquad \text{put intrinsic value} = \max(0,\; X - S)$$

$$\text{premium} = \text{intrinsic value} + \text{time value} \quad\Longrightarrow\quad \text{time value} = \text{premium} - \text{intrinsic value}$$

Properties:
- Intrinsic value is **never negative**.
- Intrinsic value is **independent of the expiration date**.
- Either part can be zero. If time value is zero the option trades **at parity** (price = intrinsic value).
- A European option can, unusually, have a **negative** time value (it can trade below parity). The book defers this to Chapter 16. Normally time value is zero or positive.
- At expiration, an option is worth **exactly its intrinsic value**: the book's one moment when "everyone ought to be able to agree" on the value.

## Worked examples (the book's)
**Call.** Underlying at \$435, April 400 call trading at \$50.
- Intrinsic value: $\max(0, 435 - 400) = 35$.
- Time value: $50 - 35 = 15$.

**Put.** Stock at \$62, October 70 put trading at \$11.
- Intrinsic value: $\max(0, 70 - 62) = 8$.
- Time value: $11 - 8 = 3$.

**Independent of expiry.** Underlying at \$83. A March 70 call and a September 70 call both have intrinsic value $83 - 70 = 13$. A June 90 put and a December 90 put both have intrinsic value $90 - 83 = 7$. (Their *prices* differ, because a longer-dated option has more time value.)

**Value at expiration** (95 call and 110 put):

| Underlying | 95 call | 110 put |
|---|---|---|
| 80 | 0 | 30 |
| 90 | 0 | 20 |
| 95 | 0 | 15 |
| 100 | 5 | 10 |
| 110 | 15 | 0 |
| 125 | 30 | 0 |

The call gains one point of value per point the underlying rises above 95; the put gains one point per point it falls below 110.

## Parity graphs (a preview of Chapter 4)
For a **buyer**, intrinsic value is a credit (they buy low and sell high). For a **seller**, it is a debit (they are forced to buy high and sell low). Plotting the position's value at expiration against the underlying price gives a **parity graph** ("parity" is another word for intrinsic value). Chapter 4 develops these.

## Common confusions
- Intrinsic value is **not** profit. Profit also depends on what you paid for the option.
- Time value is a **price**, not a time. It is the part of the premium above intrinsic value.
- An out-of-the-money option has intrinsic value 0, so its entire price is time value.

## Related
- Chapter: [[chapters/03-contract-specifications-and-option-terminology]]
- Maths needed: [[00-maths-refresher/max-function]]
- See also: [[concepts/03-contract-specifications-and-option-terminology/in-at-out-of-the-money]], [[concepts/03-contract-specifications-and-option-terminology/exercise-assignment-and-settlement]], [[glossary]], [[formulas]]
