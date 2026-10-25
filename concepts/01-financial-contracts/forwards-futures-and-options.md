# Forwards, Futures and Options

**One-line definition:** a forward fixes a price today for a trade later and both sides are obliged. A futures contract is an exchange-traded forward. An option gives one side the *right to decide later*, in return for a premium.

## Intuition
Think of three ways to buy a plot of land:

1. **Spot**: pay now, take the land now.
2. **Forward**: shake hands on the price today, pay and take the land in a year. Both must go through with it.
3. **Option**: shake hands on the price today, but *you* get to decide in a year whether to buy. The seller can't back out, and you can walk away. For that flexibility you pay a separate non-refundable amount, the **premium**.

The seller is asking for the premium because they've lost freedom: they can't sell to someone else, since you might still buy. The premium pays for that.

## Calls and puts
| | Call | Put |
|---|---|---|
| Right to | **buy** at the agreed price | **sell** at the agreed price |
| Story | Jerry's right to buy Farmer Smith's land | Jerry's right to sell his house |
| Buyer wants the market to | rise | fall |

The seller (writer) of an option takes the opposite side: obliged to sell if a call is exercised, obliged to buy if a put is exercised.

## Why they are called derivatives
Their value comes from something else:
- The *forward* on the land derives its value from the current value of the land (plus interest and other factors).
- The *call option* derives its value from the forward.
- The *put* on the house derives its value from the house.

## Insurance as a put
A home insurance policy is a put option on your house:
- **Premium** = what you pay for the policy (the seller keeps it regardless).
- **Expiration** = length of the policy.
- **Exercise price** = the insured amount (a deductible lowers it).
- **Exercise** = making a claim. You "sell" the damaged house to the insurer at the insured amount.
- If nothing happens, you simply let it expire.

Insurers price policies by estimating probabilities (house fire, car accident). Option pricing uses the same idea, which is why [[chapters/chapter-template|later chapters]] lean on probability.

## Common confusions
- *Buying a put* means you are **long the contract** but **short the market** (you gain when prices fall).
- A forward and a futures contract are the same agreement. The difference is who guarantees it and how the money moves ([[concepts/01-financial-contracts/settlement-margin-and-variation]]).
- No money changes hands when a forward or futures contract is opened, but an **option premium is paid up front**.

## Related
- Chapter: [[chapters/01-financial-contracts]]
- See also: [[glossary]]
