# Chapter 3: Contract Specifications and Option Terminology

## Summary
This chapter is the vocabulary of options. Every option is defined by five things: **type** (call or put), **underlying**, **expiration date**, **exercise price** and **exercise style** (European or American). The buyer holds all the rights and the seller all the obligations. When the buyer **exercises**, a seller is **assigned**, and the trade settles into the physical underlying, a futures position, or cash. An option's price (premium) always splits into **intrinsic value** and **time value**, and options are labelled **in, at or out of the money** by comparing the exercise price with the underlying price. The chapter ends with automatic exercise at expiration and how clearinghouses set margin for option positions.

## Key concepts
- **Type** - call (right to buy) or put (right to sell). [[concepts/03-contract-specifications-and-option-terminology/option-contract-specifications]]
- **Underlying** - 100 shares for most stock options; one futures contract for futures options. Serial and midcurve options are variations.
- **Expiration date / last trading day** - third Friday for most stock options; futures options on physical commodities usually expire a month before the futures month.
- **Exercise (strike) price** - where the underlying changes hands on exercise; set by the exchange at regular intervals.
- **Exercise style** - European (only at expiration) or American (any business day until expiration). [[concepts/03-contract-specifications-and-option-terminology/european-vs-american-exercise]]
- **Exercise / assignment** - buyer exercises, seller is assigned (chosen at random among open sellers on an exchange). [[concepts/03-contract-specifications-and-option-terminology/exercise-assignment-and-settlement]]
- **Settlement** - physical underlying (stocks), futures position (futures options), or cash (indexes).
- **Intrinsic value, time value, parity** - [[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]]
- **In / at / out of the money** - [[concepts/03-contract-specifications-and-option-terminology/in-at-out-of-the-money]]
- **Automatic exercise** - the exchange exercises in-the-money options at expiration, above a threshold, unless told not to.
- **Margining** - risk-based for options; limited risk gives capped margin. [[concepts/03-contract-specifications-and-option-terminology/option-margining]]
- **AM vs PM expiration** - settle on the opening price (many index contracts) or the closing price (stock options) on the last day.

## Formulas

**Intrinsic value** ($S$ = underlying price, $X$ = exercise price)

$$\text{call} = \max(0,\, S - X) \qquad\qquad \text{put} = \max(0,\, X - S)$$

**Premium**

$$\text{premium} = \text{intrinsic value} + \text{time value}$$

**Exercise cash flows** (for the option *exerciser*; the assigned seller gets the opposite)

| Settlement | Call exerciser | Put exerciser |
|---|---|---|
| Physical | pays $X \times \text{units}$, receives the underlying | receives $X \times \text{units}$, delivers the underlying |
| Futures | long futures at $X$; variation $(F - X) \times \text{point value} \times \text{contracts}$ | short futures at $X$; variation $(X - F) \times \text{point value} \times \text{contracts}$ |
| Cash | receives $(S - X) \times \text{point value} \times \text{contracts}$ | receives $(X - S) \times \text{point value} \times \text{contracts}$ |

Here $F$ is today's futures price. Full list in [[formulas]].

## Worked example
**Reading a contract.** "GE March 30 put": underlying 100 shares of GE, expires in March, exercise price \$30, type put. The buyer may sell 100 shares at \$30 each on or before March expiration.

**Splitting a premium.** Underlying at \$435, April 400 call at \$50: intrinsic $= \max(0, 435 - 400) = 35$, time value $= 50 - 35 = 15$. Stock at \$62, October 70 put at \$11: intrinsic $= \max(0, 70 - 62) = 8$, time value $= 11 - 8 = 3$.

**Moneyness.** Stock at \$44: \$40 call in the money by 4; \$55 put in the money by 11; \$40 put out of the money by 4; \$55 call out of the money by 11.

**Exercise cash flows.**
- Stock: exercise 1 January 110 call, pay $100 \times 110 = \$11{,}000$ and receive 100 shares.
- Futures at 85, point value \$1,000: exercise 1 February 80 call, become long one future at 80 and receive variation $(85 - 80) \times 1000 = +\$5{,}000$.
- Index at 300, \$500 per point: exercise 3 March 250 calls, receive $(300 - 250) \times 500 \times 3 = \$75{,}000$ in cash.

All the book's examples are recomputed in [[code/option_basics.ipynb]]. Full step-by-step tables are in [[concepts/03-contract-specifications-and-option-terminology/exercise-assignment-and-settlement]].

## Concepts explained in detail
- [[concepts/03-contract-specifications-and-option-terminology/option-contract-specifications]]
- [[concepts/03-contract-specifications-and-option-terminology/european-vs-american-exercise]]
- [[concepts/03-contract-specifications-and-option-terminology/exercise-assignment-and-settlement]]
- [[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]]
- [[concepts/03-contract-specifications-and-option-terminology/in-at-out-of-the-money]]
- [[concepts/03-contract-specifications-and-option-terminology/option-margining]]

## Maths I needed to recall
- [[00-maths-refresher/max-function]] - the $\max(0, \cdot)$ in intrinsic value

## Code
- [[code/option_basics.ipynb]] - intrinsic and time value, moneyness, and exercise cash flows for all three settlement types

## Open questions
- [ ] Why can a European option have negative time value? (Chapter 16, early exercise)
- [ ] Why is time value always (or nearly always) positive, and what drives its size? (later chapters)
- [ ] Which exchange will I actually trade on, and what are its strikes, expiry calendar and automatic-exercise threshold? (Chapter 3 says these differ by exchange.)
