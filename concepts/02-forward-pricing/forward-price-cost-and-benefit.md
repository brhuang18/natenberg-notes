# Forward price = cash price + costs of buying now - benefits of buying now

**One-line definition:** the fair forward price is the price that makes "buy now and hold" and "agree now, buy later" cost exactly the same, so it equals today's cash price plus what it costs to own the thing early, minus what you earn from owning it early.

## Intuition
Suppose you know you will need something in a year. You have two choices:

1. **Buy now** and hold it for a year.
2. **Agree now** to buy it in a year (a forward contract).

Both end with you owning the item in a year. They differ in what you go through meanwhile.

- Buying now means you hand over the money *early*. That money has to be borrowed (you pay interest) or could have been earning interest (you give that up). You may also pay holding costs such as storage or taxes. These are the **costs of buying now**.
- Buying now also means you own the thing *early*, so you collect anything it produces, such as dividends or rent. These are the **benefits of buying now**.

With a forward you skip both the costs and the benefits, because you do not own the item until maturity. For the forward deal to be fair, the price has to give back what you skipped:

$$\text{forward price} = \text{cash price} + \text{costs of buying now} - \text{benefits of buying now}$$

Costs push the forward price **up** (you are saved those costs, so you should pay for that). Benefits pull it **down** (you miss out on them, so you should be compensated).

## The maths
Every amount in the formula is measured **at the maturity date**. An amount paid or received earlier is carried forward to maturity with interest, using the growth factor $(1 + r \times t)$ from [[00-maths-refresher/simple-interest-and-time-fractions]]:

- A cost paid early is borrowed, so it grows by the interest on the loan.
- A benefit received early is invested, so it grows by interest earned.

The **basis** is the gap between cash and forward:

$$\text{basis} = \text{cash price} - \text{forward price}$$

Costs usually outweigh benefits, so the forward price is usually higher than the cash price and the basis is usually **negative**.

## Worked example: Jerry's land (the book's example)
Cash price \$100,000. Money costs 8% a year (borrow or lend). Forward is for 1 year.

**Costs of buying now**

| Item | Calculation | Amount |
|---|---|---|
| Interest on the purchase price | $100{,}000 \times 0.08 \times 1$ | \$8,000 |
| Property tax due in 9 months | paid in month 9 | \$2,000 |
| Interest on the tax (borrowed for the remaining 3 months) | $2000 \times 0.08 \times 3/12$ | \$40 |
| **Total costs** | | **\$10,040** |

**Benefits of buying now** (oil well pays \$500 at the end of each month)

| Item | Calculation | Amount |
|---|---|---|
| Oil revenue over 12 months | $12 \times 500$ | \$6,000 |
| Interest earned by investing each payment until month 12 | $\dfrac{500 \times 0.08}{12} \times (11 + 10 + \dots + 1 + 0) = \dfrac{500 \times 0.08}{12} \times 66$ | \$220 |
| **Total benefits** | | **\$6,220** |

(The sum $11 + 10 + \dots + 0 = 66$ is explained in [[00-maths-refresher/summation-notation]].)

**Forward price**

$$100{,}000 + 10{,}040 - 6{,}220 = 103{,}820$$

**Basis** $= 100{,}000 - 103{,}820 = -3{,}820$ (negative, as usual).

It makes no difference to Jerry or Farmer Smith whether Jerry pays \$100,000 today or agrees to pay \$103,820 in a year.

## When can the basis turn positive?
If the benefits beat the costs. Suppose the well paid \$2,000 a month instead:

- Oil revenue: $12 \times 2000 = 24{,}000$
- Interest on it: $\dfrac{2000 \times 0.08}{12} \times 66 = 880$
- Total benefits: \$24,880
- Forward price: $100{,}000 + 10{,}040 - 24{,}880 = 85{,}160$
- Basis: $100{,}000 - 85{,}160 = +14{,}840$

The forward price is now *below* the cash price. This is the same idea as backwardation, see [[concepts/02-forward-pricing/contango-backwardation-convenience-yield]].

## Why must the forward price be this? (the arbitrage argument)
The book says the two choices "should make no difference". The reason it *has* to be true is arbitrage. If the forward were, say, \$106,000, anyone could sell the forward at \$106,000, buy the land now with a loan, collect the oil, pay the tax, and deliver the land at maturity for a risk-free profit. People doing that would push the forward price back down. The same logic works in reverse for a price that is too low. Details: [[concepts/02-forward-pricing/arbitrage-and-cash-and-carry]].

## Common confusions
- **The forward price is not a forecast** of where the cash price will be. It is a cost-of-carrying calculation. Chapter 2 does not claim the cash price in a year will be \$103,820.
- **Borrowing vs lending rates.** Chapter 2 assumes one interest rate for both. In reality the borrowing rate is higher. This is handled in [[concepts/02-forward-pricing/short-selling-and-borrowing-costs]].
- **"Benefit" does not mean profit.** It is just income you receive from holding the asset (oil, dividends, coupons).

## Why it matters for options
Option values depend on the **forward price** of the underlying, not the cash price. See the end of [[chapters/02-forward-pricing]].

## Related
- Chapter: [[chapters/02-forward-pricing]]
- Instrument-specific formulas: [[concepts/02-forward-pricing/forward-price-by-instrument]]
- Maths needed: [[00-maths-refresher/simple-interest-and-time-fractions]], [[00-maths-refresher/summation-notation]]
- See also: [[glossary]], [[formulas]]
