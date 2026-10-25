# Call plus short put = a forward (a first look at put-call parity)

**One-line definition:** buying a call and selling a put with the same strike $K$ and expiration pays $S_T - K$, exactly like a forward contract to buy at $K$, so $C - P$ is pinned to the forward price.

*The book covers parity properly in Chapter 15. This note is a preview we needed to understand Chapter 7's interest-rate and short-stock discussion.*

## Intuition
A call alone pays nothing when the stock ends below $K$. A short put alone pays nothing when the stock ends above $K$. Each covers half the price range. Together they cover both halves and form a straight line.

## The payoff table
Take $K = 100$ and look at expiration:

| Final stock price $S_T$ | 80 | 90 | 100 | 110 | 120 |
|---|---|---|---|---|---|
| Long call | 0 | 0 | 0 | 10 | 20 |
| Short put | $-20$ | $-10$ | 0 | 0 | 0 |
| **Call + short put** | $-20$ | $-10$ | 0 | 10 | 20 |

The total is $S_T - K$ everywhere. That is the payoff of agreeing today to buy the stock at $K$ on the expiration date. (This is the "long call plus short put" synthetic from [[concepts/04-expiration-profit-and-loss/equivalent-positions]].)

## Pricing it
**Cost today.** You pay $C$ for the call and receive $P$ for the put, so the combination costs $C - P$.

**What a forward "buy at $K$" is worth.** The forward price $F$ is the price at which agreeing to buy costs nothing today. Compare two deals:
- Deal A: buy at $F$ on the expiration date (cost today: 0).
- Deal B: buy at $K$ on the expiration date.

Deal B is Deal A plus a guaranteed cash gain of $F - K$ at expiration (you pay $K$ instead of $F$). A guaranteed future amount is worth less today after discounting ([[00-maths-refresher/present-value-and-discounting]]), so

$$C - P = \frac{F - K}{1 + r\,t}$$

Two things have the same payoff in every scenario, so they cost the same today.

## $K$ does not have to be below $F$
$K$ is just a listed strike. The formula works for any $K$:

| Case | Deal B vs Deal A | $C - P$ | Meaning |
|---|---|---|---|
| $K < F$ | you pay less than the fair forward price | positive | call worth more than put |
| $K = F$ | same as fair forward | 0 | call and put equal |
| $K > F$ | you pay more | negative | put worth more than call |

Example: $F = 105$, $K = 110$, $1 + rt = 1.04$: $C - P = -5/1.04 = -4.81$.

## What a lower $F$ does
Only $F$ changes, so $C - P$ falls. Parity only gives the **difference**: it does not say whether the call falls, the put rises, or both. For that, compare payoffs. A lower $F$ shifts the whole price distribution down, so calls lose and puts gain. The two changes add up to the change in $C - P$, split in proportion to the deltas (call share about $\Delta_{\text{call}}$, put share about $1 - \Delta_{\text{call}}$).

## Connection to Chapter 5
In Chapter 5 we saw $E_{\text{call}} - E_{\text{put}} = F - X$ for any distribution centred on $F$ ([[formulas]]). Dividing by $1 + rt$ gives the same result.

## Common confusions
- **Parity does not tell you the call price alone.** It ties the *difference* to $F$, $K$ and the rate.
- **Simple interest.** We use $1 + rt$ as in Chapter 2. Models use continuous compounding, which changes the numbers slightly.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/long-vs-short-stock-and-option-values]]
- Maths needed: [[00-maths-refresher/present-value-and-discounting]]
- See also: [[glossary]], [[formulas]]
