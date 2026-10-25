# Option contract specifications

**One-line definition:** every option is pinned down by its **type** (call or put), **underlying**, **expiration date**, **exercise price** and **exercise style**. Together these say exactly what rights the buyer has and what obligations the seller has.

## Intuition
Think of the five items as the label on a product. Two options with different labels are different contracts that trade at different prices. Traders name them in a short-hand: *"Crude Oil October 90 call"* means underlying = October crude oil futures, expiration = October, exercise price = 90, type = call.

## The five parts

### 1. Type
- **Call**: the right to buy (take a long position in) the underlying at the exercise price.
- **Put**: the right to sell (take a short position in) the underlying at the exercise price.

Unlike a futures contract, where both sides have obligations, **all the rights lie with the option buyer and all the obligations with the seller**. If the buyer chooses to buy or sell, the seller must take the other side.

### 2. Underlying
- **Stock options:** the underlying is typically **100 shares** (a *round lot*; fewer than 100 is an *odd lot*). An exchange may change the number of shares for a very low-priced or high-priced stock to keep the contract a sensible size. *Flex options* let buyer and seller negotiate the terms.
- **Futures options:** the underlying is always **one futures contract**.
  - Usually it is the futures month matching the option's expiration month: an April option has an April future underneath.
  - **Serial options** are expirations with no matching futures month. The underlying is then the nearest futures contract *after* the option expires. For a quarterly (Mar/Jun/Sep/Dec) futures cycle:

| Option expiry | Underlying future |
|---|---|
| January or February | March |
| April or May | June |
| July or August | September |
| October or November | December |

  - **Midcurve options** are short-term options on a longer-term future (e.g. a Eurodollar future maturing in two years may sit under an option that expires in one year). They are named one-, two- or five-year midcurve by how far away the future matures.

### 3. Expiration date
The date on which the owner must make the final decision to buy (call) or sell (put). After it, all rights and obligations end.

- **Last trading day**: the last business day an option can be traded. This matters more to traders than the expiry date itself. For most stock options it is the **third Friday** of the month, the same as expiry. If that Friday is a holiday (Good Friday, occasionally), it is the preceding Thursday.
- **PM vs AM expiration:** individual stock options use the underlying's *closing* price on the last trading day (PM expiration). To avoid huge end-of-day orders from traders unwinding offsetting stock positions, many stock index contracts use the *opening* price instead (AM expiration).
- **Futures options on physical commodities** often expire days or weeks *before* the futures contract matures, because delivery takes time, commonly the month before: a March futures option expires in February, a July one in June, a November one in October. Check the exchange calendar for the exact date.

### 4. Exercise price (strike price)
The price at which the underlying changes hands if the option is exercised. The call owner **pays** it, the put owner **receives** it.

The exchange chooses the available strikes, usually at equal spacing around the current price. Example: if the underlying is at 62 when trading begins, strikes might be 50, 55, 60, 65, 70, 75. If the price later rises to 70, the exchange may add 80, 85, 90. It may also add intermediate strikes (52½, 57½, 62½, 67½).

### 5. Exercise style
European or American. See [[concepts/03-contract-specifications-and-option-terminology/european-vs-american-exercise]].

## Worked examples (from the book)
- **Crude Oil October 90 call (NYMEX):** the buyer may take a long position in **one October crude oil futures contract (1,000 barrels)** at **\$90 per barrel**, on or before October expiration.
- **GE March 30 put (CBOE):** the buyer may take a short position in **100 shares of GE** at **\$30 per share**, on or before March expiration.

## Common confusions
- **Expiration date vs last trading day.** Usually the same for stock options, but not always.
- **Stock-option expiry rules do not carry over to futures options.** A trader must look up each exchange's calendar.
- The buyer has the **choice**, the seller has the **obligation**. Buying a put is not "selling" in the sense of taking on an obligation.

## Related
- Chapter: [[chapters/03-contract-specifications-and-option-terminology]]
- Next: [[concepts/03-contract-specifications-and-option-terminology/exercise-assignment-and-settlement]]
- See also: [[concepts/01-financial-contracts/forwards-futures-and-options]], [[glossary]]
