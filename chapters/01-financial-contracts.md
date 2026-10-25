# Chapter 1: Financial Contracts

## Summary
Natenberg builds up from the simplest deal to options using one story (Jerry, Farmer Smith, and a plot of land). A **spot** deal swaps money for goods now. A **forward** agrees the price now but swaps later. An **option** is a forward where one side gets to *decide later* whether to go ahead, and pays a premium for that right. Forwards, futures and options are all **derivatives**, because their value derives from an underlying asset. The rest of the chapter covers how trades are opened and closed, what "notional value" means, how money actually moves (stock-type vs futures-type settlement), and how the exchange and clearinghouse guarantee that nobody defaults.

## Key concepts
- **Spot (cash) transaction** - agree terms, then swap money and goods immediately.
- **Forward contract** - agree terms now, swap at a later **maturity (expiration) date**. The forward price can differ from today's price, for example because the seller gives up interest on the money in the meantime.
- **Futures contract** - a forward traded on an exchange. The exchange standardises quantity, quality, delivery date and place, and payment, and guarantees the contract.
- **Option contract** - gives one party the *right* (not the obligation) to decide later. The buyer pays a **premium**, and the seller keeps it whatever the buyer decides.
  - **Call**: right to *buy*. In the story, Jerry's right to buy the land.
  - **Put**: right to *sell*. In the story, Jerry's right to sell his house.
- **Insurance is a put option.** The policy holder can "sell" the damaged house back at the insured amount. The premium, the expiry date and the exercise price (insured amount, possibly with a deductible) all have option equivalents.
- **Derivative** - a contract whose value depends on an underlying asset. Natenberg focuses on forwards, futures and options. **Swaps** (exchanging cash flows, e.g. fixed vs floating interest) are mostly off-exchange and skipped.
- **Opening vs closing trade** - the first trade creates an open position. A later trade that reverses it is the closing trade. Profit does not depend on the order: buy low then sell high, or sell high then buy low.
- **Open interest** - number of contracts not yet closed out. Longs always equal shorts, since every buyer has a seller.
- **Long / short** - after an opening trade you are *long* (bought first) or *short* (sold first). Long usually costs money (debit), short usually receives money (credit).
- **Contract position vs market position** - for derivatives these can differ. Someone *long a put* has bought a contract, but wants the market to *fall*. Natenberg uses "long/short contract position" for what you traded and "long/short market position" for which way you want the market to move.
- **Notional value** - the value of the goods a forward/futures contract covers. No cash changes hands at the start, so this is a measure of size, not a price paid.
- **Stock-type vs futures-type settlement** - see [[concepts/01-financial-contracts/settlement-margin-and-variation]].
- **Clearinghouse** - see [[concepts/01-financial-contracts/clearinghouse-and-counterparty-risk]].

## Formulas

**Notional value (physical commodity)**

$$\text{notional value} = \text{units delivered} \times \text{unit price}$$

Example: $1{,}000 \times \$75 = \$75{,}000$.

**Notional value (cash-settled index or similar)**

$$\text{notional value} = \text{index price} \times \text{point value}$$

Example: $825.00 \times \$200 = \$165{,}000$.

**Variation on a futures position** (per day, as the price moves)

$$\text{variation} = (\text{new price} - \text{old price}) \times \text{units per contract} \times \text{number of contracts}$$

Use a positive number of contracts for long and a negative number for short. A positive result is a credit, and a negative result is a debit.

## Worked example: Jerry's story as contracts

| Jerry's situation | Contract | Who has the choice? |
|---|---|---|
| Buys land from Farmer Smith for \$100,000 today | Spot | Nobody, deal done now |
| Agrees to buy it in one year at an agreed price | Forward | Neither, both are obliged |
| Gets one year to decide whether to buy at that price, and pays Farmer Smith a separate amount for waiting | **Call** (Jerry bought it, Smith sold it) | Jerry |
| Gets one year to decide whether to *sell* his house to the young couple at an agreed price, paying them an amount for their trouble | **Put** (Jerry bought it, the couple sold it) | Jerry |

Why the seller wants paying: Farmer Smith cannot accept other offers for the land for a year because he must hold it in case Jerry buys. He is "a hostage to Jerry's final decision", and the premium compensates him. Whatever Jerry decides, Smith keeps the premium.

## Worked example: futures settlement (the book's Figure 1-2, step by step)

Contract: 1,000 units, margin \$3,000 per contract. Start with a short position of 9 contracts opened at \$75.

| Day | Price | Trade | Position after | Variation | Running realized P&L |
|---|---|---|---|---|---|
| 1 | 75 | sell 9 (opening) | short 9 | 0 | 0 |
| 2 | 77 | none | short 9 | $(77-75)\times(-9)\times1000 = -\$18{,}000$ | $-\$18{,}000$ |
| 3 | 74 | buy 2 | short 7 | $(74-77)\times(-9)\times1000 = +\$27{,}000$ | $+\$9{,}000$ |
| 4 | 70 | buy 4 | short 3 | $(70-74)\times(-7)\times1000 = +\$28{,}000$ | $+\$37{,}000$ |
| 5 | 80 | buy 3 (closing) | flat | $(80-70)\times(-3)\times1000 = -\$30{,}000$ | $+\$7{,}000$ |

Check against the trades themselves: sold 9 at 75. Bought 2 at 74 (+\$2,000), 4 at 70 (+\$20,000) and 3 at 80 (-\$15,000). Total is +\$7,000, which matches.

Margin required each day is \$3,000 times the contracts still open (\$27,000, \$27,000, \$21,000, \$9,000, then 0).

## Open interest, clearing and who guarantees what
Exchange-traded contracts break the buyer-seller link: the exchange becomes the seller to every buyer and the buyer to every seller. Details in [[concepts/01-financial-contracts/clearinghouse-and-counterparty-risk]].

## Concepts explained in detail
- [[concepts/01-financial-contracts/forwards-futures-and-options]]
- [[concepts/01-financial-contracts/settlement-margin-and-variation]]
- [[concepts/01-financial-contracts/clearinghouse-and-counterparty-risk]]

## Maths I needed to recall
- Only arithmetic and signs (a negative number of contracts means short). No refresher needed yet.

## Code
- None yet. A small notebook that tracks margin, variation and P&L day by day would be a good exercise.

## Open questions
- [x] Why should the forward price include interest and carrying costs? Answered in [[chapters/02-forward-pricing]]: buying now means paying early and owning early, and the forward price must make the two routes equal.
- [ ] How are options priced from probabilities? (The chapter only hints: Chapter 5.)
