# Option margining (limited vs unlimited risk)

**One-line definition:** the margin the clearinghouse asks for on an option position depends on how much the position can lose. Limited risk means margin is capped; unlimited risk means the clearinghouse must judge the risk across many possible market moves.

## Intuition
Margin is a security deposit against losses ([[concepts/01-financial-contracts/settlement-margin-and-variation]]). For a futures contract the exchange can set one fixed deposit per contract. Options are more varied, so there is no single number. The first question is: *is there a worst case?*

## The ideas
- **Limited risk.** The most an option **buyer** can lose is the premium paid, so the clearinghouse never requires more margin than that. Even for a complicated position, if there is a maximum possible loss, there is a maximum margin.
- **Unlimited risk.** Some positions could lose without bound (a sold call is the classic case, see the illustration below). The clearinghouse analyses many possible outcomes and sets margin "commensurate with the perceived risk".
- **No single formula.** Unlike futures, there is no fixed deposit per option position. All methods are **risk-based**: they examine the position under a broad range of market conditions.
- **Two well-known systems:**
  - **OCC** (Options Clearing Corporation): risk-based margining for US stock and index options.
  - **SPAN** (Standard Portfolio Analysis of Risk, developed by the CME): the most widely used system on futures exchanges.
  - Both build an **array of scenarios** over (a) the underlying price and (b) how fast the price might change, then use the array to set the requirement.

## Our own illustration (not in the book)
Sell a 100 call for a premium of 5. The position's profit at expiration is $5 - \max(0, S - 100)$.

| Underlying at expiry | Profit |
|---|---|
| 90 | $+5$ |
| 100 | $+5$ |
| 150 | $5 - 50 = -45$ |
| 300 | $5 - 200 = -195$ |

The loss keeps growing with the price, so no fixed margin number can cover every outcome. Compare a **bought** 100 call for 5: the worst case is $-5$ whatever happens.

## Common confusions
- **Margin vs premium:** premium is the price of the option; margin is collateral.
- Whether an option is paid for in full (stock-type) or margined (futures-type) is separate from the risk-based margin on short positions. See [[concepts/01-financial-contracts/settlement-margin-and-variation]].

## Related
- Chapter: [[chapters/03-contract-specifications-and-option-terminology]]
- See also: [[concepts/01-financial-contracts/clearinghouse-and-counterparty-risk]], [[glossary]]
