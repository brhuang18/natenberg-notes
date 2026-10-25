# Chapter 2: Forward Pricing

## Summary
A forward contract does not make the costs and benefits of owning something disappear, it just *postpones* them, so those costs and benefits must show up in the forward price. The chapter's one big idea is **forward price = cash price + costs of buying now - benefits of buying now**. Natenberg then applies it to physical commodities, stocks, bonds and currencies, shows how to *infer* a missing input (an implied rate or dividend) from a market price, and explains why a mispriced forward lets traders lock in an **arbitrage** profit. He finishes with the practical details that bend the neat formulas: dividend dates and the extra cost of selling stock short. For options, this matters because option pricing uses the **forward price** of the underlying (see "Why this matters" below).

## Key concepts
- **Forward price** - the fair price today for a purchase at a future date. Detail: [[concepts/02-forward-pricing/forward-price-cost-and-benefit]]
- **Costs / benefits of buying now** - what you pay or earn by owning the item early (interest, storage, insurance, taxes vs dividends, coupons, oil revenue). Both are carried to maturity with interest.
- **Basis** - cash price minus forward price. Usually negative.
- **Contango (normal market)** - forward prices above cash. **Backwardation** - cash above forward. [[concepts/02-forward-pricing/contango-backwardation-convenience-yield]]
- **Convenience yield** - the extra value the market gives to holding a physical commodity right now. It is inferred, not quoted.
- **Forward rate / FRA** - an interest rate that starts at a future date; a forward-rate agreement locks one in. Example: a "$3 \times 9$" rate is a six-month rate starting in three months.
- **Futures price = forward price.** A futures contract is a forward, so no calculation is needed for futures options. For exchange-traded options on commodities, bonds and currencies, the underlying is usually the futures contract.
- **Arbitrage** - trading the same or closely related things in different markets to profit from a mispricing; **cash-and-carry** buys cash, sells forward, and carries to maturity. A *carry trade* is not true arbitrage. [[concepts/02-forward-pricing/arbitrage-and-cash-and-carry]]
- **Implied value** - an input recovered by running a pricing formula backwards. [[concepts/02-forward-pricing/implied-values]]
- **Dividend dates** - declared, ex-dividend, record, payable. [[concepts/02-forward-pricing/stock-dividends-and-key-dates]]
- **Short sale, short-stock rebate, long rate $r_l$, short rate $r_s$, borrowing cost $r_{bc}$** - [[concepts/02-forward-pricing/short-selling-and-borrowing-costs]]
- **OTC (over-the-counter)** - trading that does not happen on an organised exchange.

## Formulas
Notation: $t$ = years to maturity, $r$ = annual rate as a decimal. Full list with symbols in [[formulas]].

**General idea**

$$\text{forward price} = \text{cash price} + \text{costs of buying now} - \text{benefits of buying now}$$

**Physical commodity**

$$F = C(1 + rt) + st + it$$

**Stock** (exact, then simplified)

$$F = S(1 + rt) - \sum_n d_n(1 + r_n t_n) \qquad\qquad F \approx S(1 + rt) - D$$

**Bond or note** (coupons $c_n$ replace dividends)

$$F = B(1 + rt) - \sum_n c_n(1 + r_n t_n)$$

**Foreign currency** (domestic per foreign unit)

$$F = S \times \frac{1 + r_d t}{1 + r_f t}$$

**Implied values** (from $F = S(1+rt) - D$)

$$S = \frac{F + D}{1 + rt} \qquad r = \frac{\frac{F + D}{S} - 1}{t} \qquad D = S(1 + rt) - F$$

**Short-sale band** (stock, no-arbitrage range for someone who must borrow stock)

$$S(1 + r_s t) - D \;\le\; F \;\le\; S(1 + r_l t) - D$$

## Worked example
**1. Jerry's land.** Cash price \$100,000, rate 8%, one year. Costs of buying now: interest \$8,000 + property tax \$2,000 + interest on the tax \$40 = \$10,040. Benefits: oil \$6,000 + interest on it \$220 = \$6,220.

$$F = 100{,}000 + 10{,}040 - 6{,}220 = 103{,}820 \qquad \text{basis} = 100{,}000 - 103{,}820 = -3{,}820$$

**2. A stock and an arbitrage check.** $S = 67.00$, 8 months, $r = 6\%$, dividends $D = 0.66$.

$$F_{\text{fair}} = 67.00 \times (1 + 0.06 \times \tfrac{8}{12}) - 0.66 = 69.68 - 0.66 = 69.02$$

If the market's 8-month forward is **69.50** (too high), sell it, buy the stock with borrowed money, collect the dividends, deliver the stock: profit $-2.68 + 0.66 + 69.50 - 67.00 = +0.48 = 69.50 - 69.02$. If instead you decide the market is right and your *interest rate* is wrong, the implied rate is $\left(\frac{69.50 + 0.66}{67.00} - 1\right) / \tfrac{8}{12} = 7.07\%$, and the implied dividend (if you trust the rate) is only \$0.18.

**3. Short-sale band.** With a short rate of 4%, the lower edge is $67.00(1 + 0.04 \times \tfrac{8}{12}) - 0.66 = 68.13$. A trader without stock can only profit if the forward is below 68.13 or above 69.02. At 68.75, a stock *owner* gains +0.27 but a short seller loses 0.62.

All of these are recomputed in [[code/forward_pricing.ipynb]]. Step-by-step versions: [[concepts/02-forward-pricing/forward-price-cost-and-benefit]], [[concepts/02-forward-pricing/forward-price-by-instrument]], [[concepts/02-forward-pricing/arbitrage-and-cash-and-carry]], [[concepts/02-forward-pricing/implied-values]], [[concepts/02-forward-pricing/short-selling-and-borrowing-costs]].

## Why this matters for options
Option values depend on the **forward price** of the underlying, not just today's price. The book says in Chapter 5 that "the forward price of the underlying contract plays a central role in all option pricing models", and that for European options the current price only matters as a way to get the forward price. That is why this chapter comes before any option pricing.

## Concepts explained in detail
- [[concepts/02-forward-pricing/forward-price-cost-and-benefit]]
- [[concepts/02-forward-pricing/forward-price-by-instrument]]
- [[concepts/02-forward-pricing/contango-backwardation-convenience-yield]]
- [[concepts/02-forward-pricing/arbitrage-and-cash-and-carry]]
- [[concepts/02-forward-pricing/implied-values]]
- [[concepts/02-forward-pricing/short-selling-and-borrowing-costs]]
- [[concepts/02-forward-pricing/stock-dividends-and-key-dates]]

## Maths I needed to recall
- [[00-maths-refresher/simple-interest-and-time-fractions]] - interest over part of a year, the growth factor $1 + rt$
- [[00-maths-refresher/rearranging-formulas]] - solving for $S$, $r$, $D$, $C$
- [[00-maths-refresher/summation-notation]] - the $\sum$ sign and adding $1 + 2 + \dots + n$

## Code
- [[code/forward_pricing.ipynb]] - every worked example above, with editable inputs

## Notes on the book's text
- The currency example in the PDF prints the growth ratio as "1.30 / 1.02". It should be 1.03 / 1.02 (the result 1.5147 only works with 1.03).
- The book's currency derivation also says "invest $C_d$ at $r_f$"; it should be $r_d$ for the domestic currency.
- The settlement and ex-dividend rules (T+3) are out of date for US stocks, which now settle T+1. See [[concepts/02-forward-pricing/stock-dividends-and-key-dates]].

## Open questions
- [x] Why should the forward price include interest and carrying costs? (Raised in Chapter 1.) Answered above: buying now means paying early and owning early, and the forward price must make the two routes equal.
- [ ] Chapter 2 uses simple interest, $1 + rt$. Which form do later models use (continuous compounding, $e^{rt}$) and how much does it change the forward price?
- [ ] How is the forward price actually used to calculate an option's theoretical value? (Chapter 5)
- [ ] What happens to the short-sale band when a stock is "hard to borrow" and the rebate is near zero?
