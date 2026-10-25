# Interest-rate products: rate volatility vs price volatility

**One-line definition:** for contracts quoted as $100$ minus an interest rate (such as Eurodollar futures), volatility is measured on the *rate*, not on the quoted price, and calls and puts swap roles when the model works in rate terms.

## Intuition
A Eurodollar futures contract is quoted as 100 minus the interest rate. If the interest rate is 7.00%, the contract trades at $100 - 7.00 = 93.00$. Euribor works the same way: 4.50% gives 95.50.

The quote is built this way so that these contracts move like bond prices: rates up, price down.

A price of 93 with a 26% volatility does *not* mean a one-standard-deviation move of 26% of 93. The percentage refers to the **rate** (7.00), which is what is actually fluctuating.

## The maths
Use $(100 - \text{price})$ in place of the price:

$$\text{daily st. dev.} \approx (100 - \text{price}) \times \frac{\sigma}{16} \qquad \text{weekly st. dev.} \approx (100 - \text{price}) \times \frac{\sigma}{7.2}$$

## Worked example (the book's)
Eurodollar futures at 93.00, volatility 26%.
- Rate $= 100 - 93.00 = 7.00$.
- Daily: $7.00 \times 0.26 / 16 = 0.11$.
- Weekly: $7.00 \times 0.26 / 7.2 = 0.25$.

(For comparison, applying 26% to the quoted price 93 would give $93 \times 0.26/16 = 1.51$ a day, about 14 times too large.)

## Exercise prices flip, and so do calls and puts
To be consistent, the exercise price is also indexed from 100. A listed 93.00 exercise price is really a 7.00% (rate) exercise price.

Then calls and puts swap:
- A listed **93.00 call** pays off if the contract rises above 93.00.
- A rise in the contract means the **rate falls** below 7.00%.
- So the listed 93.00 call is a **7.00% put** in rate terms.

A model set up correctly for these contracts does this automatically: subtract the underlying price and the exercise price from 100, and treat listed calls as puts and listed puts as calls.

## Bonds and notes are different
Bond and note prices are not capped like this (they can exceed 100 depending on the coupon), so options on bond and note futures are usually valued with a traditional model on the price. Interest-rate products can still need special models.

## Yield volatility vs price volatility
For a bond you can compute volatility two ways, and traders keep them apart:
- **Price volatility:** from the instrument's market price.
- **Yield volatility:** from the yield calculated from its price. The exercise price must then also be expressed as a yield.

## Common confusions
- **Do not apply a rate volatility to the quoted price.** Use $100 -$ price.
- **Calls and puts swap** only when the model works in rate terms. Listed calls are still calls in the market.
- This is a niche case: for stocks and ordinary commodities, apply volatility to the price.

## Related
- Chapter: [[chapters/06-volatility]]
- Previous: [[concepts/06-volatility/checking-volatility-against-price-changes]]
- Next: [[concepts/06-volatility/lognormal-distributions]]
- Scaling: [[concepts/06-volatility/scaling-volatility-for-time]]
- Chapter 5 mention of Eurodollar futures as an interest rate benchmark: [[concepts/05-theoretical-pricing-models/choosing-the-inputs]]
- See also: [[glossary]]
