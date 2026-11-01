# Submitting a spread order

**One-line definition:** in option markets a whole spread, however complicated, is often traded **as one order at one price**: one bid and one ask for the entire package, with no concern about how the price splits across the legs.

## Intuition
Chapter 10 introduced the idea that only the **total** price of a spread matters ([[concepts/10-introduction-to-spreading/executing-a-spread]]). In option markets this is routine. A market maker quotes a straddle as, say, **6.25 / 6.75**:

- You **sell** the straddle at the bid, 6.25.
- You **buy** it at the ask, 6.75.

If you buy at 6.75, neither you nor the market maker cares whether the call cost 3.75 and the put 3.00, or the call 2.00 and the put 4.75. The only requirement is that **the two prices add to 6.75**. The spread's bid-ask width is $6.75 - 6.25 = 0.50$.

## Market makers and complexity
A market maker will always try to give you one bid and one ask for the entire spread.
- For common spreads (straddles, strangles, butterflies, calendars) a quote can come very quickly.
- For very complex spreads (several options in unusual ratios) it may take **several minutes** to calculate. But the market maker will still make an effort to give his best two-sided market.

## What a platform lets you do
- **Electronic exchanges** usually let you submit spreads for the most common types: simple call or put spreads, straddles, strangles, calendars.
- **More complex spreads** (butterflies, Christmas trees, unusual ratios) must be executed **piece by piece** or sent to a **broker** on an open-outcry exchange, where the exact description can be given directly to market makers.

## Order types
A spread order is most often:
- a **market order** (fill at the current market price), or
- a **limit order** (fill only at a specified price or better).

It can also carry a **contingency** instruction. The book lists these, all defined in its Appendix A: all or none; fill or kill; immediate or cancel; market if touched; market on close; not held; one cancels the other; stop limit; stop loss.

A broker must follow any special instructions. Unless you know market conditions well or trust the broker, **it may be wise to give specific instructions**.

## Communication risk
A spread order has many pieces of information: quantity, expiration months, exercise prices, call or put, and buy or sell. It is easy to transmit something incorrectly. The book's advice: **double-check all orders before submitting.** "Option trading can be difficult enough without the additional problems of miscommunication."

## Common confusions
- **A spread price is not the sum of independent trades.** The leg prices are decided by the market maker; you only see the total.
- **Leg risk** (Chapter 10) disappears if the spread executes as a single order; it comes back if you must trade piece by piece.
- **The spread's bid-ask is not the sum of the legs' bid-asks** in general; it is whatever the market maker quotes for the package.

## Related
- Chapter: [[chapters/11-volatility-spreads]]
- Previous: [[concepts/11-volatility-spreads/adjusting-a-volatility-spread]]
- Earlier: [[concepts/10-introduction-to-spreading/executing-a-spread]]
- See also: [[glossary]], [[formulas]]
