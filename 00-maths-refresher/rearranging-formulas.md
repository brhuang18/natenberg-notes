# Rearranging formulas (solving for the unknown)

**One-line summary:** to get a letter on its own, undo the operations around it, in reverse order, doing the same thing to both sides each time.

Used in: [[concepts/02-forward-pricing/implied-values]], [[concepts/02-forward-pricing/forward-price-by-instrument]], [[chapters/02-forward-pricing]]

## Intuition
An equation is a balanced set of scales. You can add, subtract, multiply or divide anything you like, as long as you do the **same thing to both sides**. The balance never breaks. To isolate a letter, peel away what surrounds it the way you would unwrap a parcel: the last thing wrapped on is the first thing taken off.

## The method
1. Find the letter you want (the "unknown").
2. Look at what is attached to it. The operation that was applied **last** when building the formula is the first one you undo.
3. Undo it on **both** sides. Addition is undone by subtraction, multiplication by division, and vice versa.
4. Repeat until the unknown stands alone.
5. Check by plugging numbers back in.

## Worked example 1: solve for the stock price $S$
Start from the forward price of a stock (Chapter 2):

$$F = S \times (1 + r t) - D$$

$S$ is multiplied by $(1+rt)$, and then $D$ is subtracted. The last thing done was "subtract $D$", so undo that first.

| Step | What we do | Result |
|---|---|---|
| 1 | Add $D$ to both sides (undoes "minus $D$") | $F + D = S \times (1 + rt)$ |
| 2 | Divide both sides by $(1 + rt)$ (undoes "times $(1+rt)$") | $\dfrac{F + D}{1 + rt} = S$ |

So $S = \dfrac{F + D}{1 + rt}$.

Check with the book's numbers: $F = 69.50$, $D = 0.66$, $r = 0.06$, $t = 8/12$, so $1 + rt = 1.04$. Then $S = (69.50 + 0.66)/1.04 = 67.46$.

## Worked example 2: solve for the interest rate $r$
Start from the line we reached in example 1:

$$F + D = S \times (1 + rt)$$

| Step | What we do | Result |
|---|---|---|
| 1 | Divide both sides by $S$ | $\dfrac{F + D}{S} = 1 + rt$ |
| 2 | Subtract 1 from both sides | $\dfrac{F + D}{S} - 1 = rt$ |
| 3 | Divide both sides by $t$ | $r = \dfrac{\dfrac{F + D}{S} - 1}{t}$ |

Check: $(69.50 + 0.66)/67.00 = 1.04716$. Subtract 1 to get $0.04716$. Divide by $t = 8/12$ (the same as multiplying by 1.5) to get $0.0707$, i.e. 7.07%.

## Worked example 3: solve for the dividend $D$
Start again from $F = S(1+rt) - D$. The unknown $D$ is being *subtracted*, which is a little awkward.

| Step | What we do | Result |
|---|---|---|
| 1 | Add $D$ to both sides | $F + D = S(1+rt)$ |
| 2 | Subtract $F$ from both sides | $D = S(1+rt) - F$ |

Check: $67.00 \times 1.04 - 69.50 = 69.68 - 69.50 = 0.18$.

## Worked example 4: solve for the commodity cash price $C$
From $F = C(1 + rt) + (s + i)t$:

| Step | What we do | Result |
|---|---|---|
| 1 | Subtract $(s+i)t$ from both sides | $F - (s+i)t = C(1+rt)$ |
| 2 | Divide both sides by $(1+rt)$ | $C = \dfrac{F - (s+i)t}{1 + rt}$ |

## Common confusions
- **Forgetting to apply the step to the *whole* side.** Dividing both sides by $(1+rt)$ means the *entire* left side is divided, so you need brackets: $(F + D)/(1 + rt)$, not $F + D/(1+rt)$.
- **Order matters.** In example 1, dividing by $(1+rt)$ *before* adding $D$ gives a wrong answer unless you also divide $D$.
- **Always check with numbers.** If plugging the answer back into the original formula does not reproduce the starting value, there is a slip somewhere.

## Related
- Previous: [[00-maths-refresher/simple-interest-and-time-fractions]]
- Index: [[00-maths-refresher/README|Maths refresher]]
