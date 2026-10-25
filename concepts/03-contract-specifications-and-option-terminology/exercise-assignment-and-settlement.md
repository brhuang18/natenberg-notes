# Exercise, assignment and settlement

**One-line definition:** the option **buyer exercises** to turn the option into a position in the underlying; the **seller is assigned** the other side. That position is then **settled** in one of three ways: physical underlying, a futures position, or cash.

## Intuition
Exercising is the buyer pressing the button on the right they paid for. Assignment is the seller receiving the consequence. Settlement is how the resulting trade is carried out, and it depends on what the underlying is. You cannot hand over a stock index, so index options settle in cash; a futures option gives you a futures position, which is a "paper" contract.

## Who does what
To exercise, the buyer sends an **exercise notice** (to the dealer, or to the exchange for exchange-traded options). A valid notice means the seller has been **assigned**.

| If you... | You... |
|---|---|
| **Exercise a call** | choose to **buy** at the exercise price |
| **Are assigned on a call** | are required to **sell** at the exercise price |
| **Exercise a put** | choose to **sell** at the exercise price |
| **Are assigned on a put** | are required to **buy** at the exercise price |

On an exchange the link between buyer and seller is broken (the clearinghouse stands in the middle, see [[concepts/01-financial-contracts/clearinghouse-and-counterparty-risk]]). The exchange assigns someone who has **sold that option and not closed the position**. Beyond that, who is picked is essentially **random**. Once exercised, the option's rights and obligations end, just as if it had expired.

## 1. Settlement into the physical underlying
Call exerciser pays the exercise price and receives the underlying; put exerciser receives the exercise price and delivers the underlying. **Stock options always settle this way** (100 shares per option).

| Action | Cash | Shares |
|---|---|---|
| Exercise 1 January 110 call | pay $100 \times 110 = \$11{,}000$ | receive 100 |
| Assigned on 6 April 40 calls | receive $600 \times 40 = \$24{,}000$ | deliver 600 |
| Exercise 2 July 60 puts | receive $200 \times 60 = \$12{,}000$ | deliver 200 |
| Assigned on 3 October 95 puts | pay $300 \times 95 = \$28{,}500$ | receive 300 |

**Key point:** the cash flow depends **only on the exercise price**, not on the stock price. Whether the stock is at \$10 or \$1,000, the call exerciser pays the exercise price. (Profit or loss still depends on the stock price and what was paid for the option.)

## 2. Settlement into a futures position
Exercise is like buying or selling the futures contract **at the exercise price**. The position is immediately **futures-type** ([[concepts/01-financial-contracts/settlement-margin-and-variation]]): a margin deposit is required, and a variation payment arrives straight away because the futures price is different from the exercise price.

Setup: futures at **85.00**, point value **\$1,000**, margin **\$3,000** per contract. Variation $= (\text{futures price} - \text{position price}) \times \text{point value} \times \text{contracts}$, with contracts negative for a short.

| Action | New position | Margin | Variation |
|---|---|---|---|
| Exercise 1 February 80 call | long 1 at 80 | \$3,000 | $(85-80) \times 1000 = +\$5{,}000$ |
| Assigned on 6 May 75 calls | short 6 at 75 | $6 \times 3000 = \$18{,}000$ | $(75-85) \times 1000 \times 6 = -\$60{,}000$ |
| Exercise 4 August 100 puts | short 4 at 100 | $4 \times 3000 = \$12{,}000$ | $(100-85) \times 1000 \times 4 = +\$60{,}000$ |
| Assigned on 2 November 95 puts | long 2 at 95 | $2 \times 3000 = \$6{,}000$ | $(85-95) \times 1000 \times 2 = -\$20{,}000$ |

Check the first row with the Chapter 1 formula: long 1 contract opened at 80, price now 85, so variation $= (85 - 80) \times 1000 \times 1 = +5000$. For the second row a short position has contracts $= -6$: $(85 - 75) \times 1000 \times (-6) = -60000$, the same as in the table.

Notice the variation credit for an exerciser is exactly the option's **intrinsic value** ($85 - 80 = 5$ points for the 80 call).

## 3. Settlement into cash
Used mainly for **index** contracts where delivery is impractical. No position results; there is a cash payment equal to the difference between the exercise price and the underlying's value at the end of the trading day.

Setup: index fixed at **300**, **\$500 per index point**.

| Action | Cash |
|---|---|
| Exercise 3 March 250 calls | $(300-250) \times 500 \times 3 = +\$75{,}000$ |
| Assigned on 7 June 275 calls | $(275-300) \times 500 \times 7 = -\$87{,}500$ |
| Exercise 2 September 320 puts | $(320-300) \times 500 \times 2 = +\$20{,}000$ |
| Assigned on 4 December 340 puts | $(300-340) \times 500 \times 4 = -\$80{,}000$ |

## Automatic exercise
At expiration, an in-the-money option always has some intrinsic value. In the early days of exchange trading, forgetting to submit the exercise notice meant an in-the-money option expired worthless, which no one wants. So most exchanges now **exercise automatically** any in-the-money option at expiration.

- Exchanges usually set a **threshold**, since exercising an option that is only slightly in the money may not cover transaction costs. With a threshold of 0.05: an option 0.06 in the money is exercised automatically; one 0.03 in the money is not, but the holder *may* still exercise by submitting an exercise notice.
- A holder who does not want an in-the-money option exercised can send a **do not exercise notice**.
- Thresholds can differ between retail customers and professionals (the book's example: 0.05 for retail, 0.02 for professionals).

## Common confusions
- **Exercise vs assignment:** the *buyer* exercises, the *seller* is assigned. Sellers have no say.
- **Long vs short results:** exercising a *put* leaves you **short** the underlying; being assigned on a *call* leaves you **short** (you sold).
- **Futures-option "margin" is not a cost**; it is a deposit, and the variation is the real cash. Compare [[concepts/01-financial-contracts/settlement-margin-and-variation]].
- Exercising an option early (American style) throws away any time value left, see [[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]].

## Related
- Chapter: [[chapters/03-contract-specifications-and-option-terminology]]
- Before: [[concepts/03-contract-specifications-and-option-terminology/option-contract-specifications]]
- See also: [[concepts/03-contract-specifications-and-option-terminology/european-vs-american-exercise]], [[glossary]], [[formulas]]
