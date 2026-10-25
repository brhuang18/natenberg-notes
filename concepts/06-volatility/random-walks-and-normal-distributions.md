# Random walks and normal distributions

**One-line definition:** a random walk is a path made of unpredictable steps; when many such walks are collected, their end points pile up in a symmetric bell shape called the normal distribution, and the *width* of that bell is what we call volatility.

## Intuition
Picture a pinball maze (the book's Figure 6-1, a "quincunx" or Galton board). A ball drops through rows of nails. At each nail it goes left or right with a 50% chance each. You cannot predict one ball's path. But drop thousands of balls and a clear pattern appears:

- most land near the middle,
- fewer land farther out,
- very few land in the far troughs.

The pile is bell-shaped: **symmetrical**, with its **peak in the centre**, and **tails that fall away** on both sides. That is a **normal distribution**.

Now relate the maze to a price:
- the ball's **sideways** movement is the **price going up or down**,
- the ball's **downward** movement is **time passing**.

If prices follow a random walk, the pile at the bottom is the distribution of prices at expiration.

## Same shape, different width
Change the nails and the bell changes (the book's Figures 6-2 to 6-4):

| Maze | What happens to a ball | Bell | Market it represents |
|---|---|---|---|
| Figure 6-3 | Sideways movement is restricted (it falls two levels between nails) | tall and narrow | **low** volatility |
| Figure 6-2 | The standard maze | medium | **moderate** volatility |
| Figure 6-4 | Each step moves two nails sideways | low and wide | **high** volatility |

All three are still normal distributions. They differ only in how fast they spread out. That spread is what we will measure with the standard deviation ([[concepts/06-volatility/mean-and-standard-deviation]]).

![Three bells of different widths, with the area beyond a strike shaded](../../images/ch06-spread-and-call-value.png)

## Why the width changes option values
It may seem the choice of bell does not matter. Every normal curve is symmetric, so extra chance of a big up move is balanced by extra chance of a big down move. The catch (the book's key point):

- The expected value of the **underlying** depends on *all* outcomes, so the balance holds and the mean stays put.
- The expected value of an **option** depends only on outcomes where it finishes **in the money**. Everything else is worth zero.

So take a call with an exercise price above today's price. Its value depends on the part of the bell to the **right of the exercise price**. A wider bell puts more area there, so the call is worth more. In the picture above, the chance of finishing above 110 is about 10.6% (low), 23.8% (moderate) and 33.8% (high).

The same wide bell puts more area to the **left** of a low exercise price, so puts gain too. Because the bells are symmetric: **in a high-volatility market all options, calls and puts, at every exercise price, are worth more. In a low-volatility market they are worth less.**

## Common confusions
- **Volatility is not direction.** A wide bell is centred just as before. It says "bigger moves either way", not "the price will go up".
- **The coin-flip picture is only an analogy.** The book says Figure 6-2 could represent 15 coin flips. Real 15-flip results are narrower than the book's drawn curve; see [[chapters/06-volatility]] (notes on the book's text).
- **Normal does not mean "ordinary".** It is the technical name for the bell shape.

## Related
- Chapter: [[chapters/06-volatility]]
- Maths needed: [[00-maths-refresher/normal-distribution-and-z-scores]], [[00-maths-refresher/probability-and-expected-value]]
- Earlier: [[concepts/05-theoretical-pricing-models/direction-and-speed]], [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]] (spread raised the call's value there too)
- Next: [[concepts/06-volatility/mean-and-standard-deviation]]
- Code: [[code/volatility.ipynb]]
- See also: [[glossary]]
