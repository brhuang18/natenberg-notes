# Long vs short stock: why the hedge changes the option's value

**One-line definition:** the interest rate that belongs in the model depends on whether the trader hedges with long stock (ordinary rate $r_l$) or short stock (lower short rate $r_s$), so the same option has a slightly different value for different traders.

## The puzzle
In theory an option has one value. Why would it depend on whether a trader is long or short stock? Because the model's value is really **the cost of replicating the option** by hedging with stock, and that cost depends on how the hedge is financed.

## The chain of logic
1. **Option value is anchored to the forward price $F$.** A higher $F$ means calls are worth more and puts less.
2. **$F$ depends on the cost of carrying the stock.** For a stock with one dividend $D$:

$$F = S\,(1 + r\,t) - D$$

3. **The rate depends on which side of stock you are on.**
   - **Long stock:** you finance at the ordinary rate $r_l$.
   - **Short stock:** you sell borrowed shares and the broker holds the cash. You earn only the short rate $r_s = r_l - r_{bc}$ on it ([[concepts/02-forward-pricing/short-selling-and-borrowing-costs]]).

   Book numbers: $S = 67$, 8 months, $D = 0.66$, $r_l = 6\%$, $r_s = 4\%$.

$$F_{\text{long}} = 67\left(1 + 0.06 \cdot \tfrac{8}{12}\right) - 0.66 = 69.02 \qquad F_{\text{short}} = 67\left(1 + 0.04 \cdot \tfrac{8}{12}\right) - 0.66 = 68.13$$

4. **A lower $F$ lowers calls and raises puts.** See [[concepts/07-risk-measurement-i/synthetic-forward-and-put-call-parity]]: $C - P = \dfrac{F - K}{1 + rt}$ shrinks when $F$ falls, and calls and puts split that shrinkage in proportion to their deltas.

## Why *your position* picks the rate: the marginal share
The relevant rate is set by the **next share you trade**, not by the stock you hold on average.

Suppose you already hold a **short stock** position and you **sell a call**. A short call has negative delta, so you hedge by **buying stock**. But buying stock covers some of your short, which means you give up interest at the short rate $r_s$ you were earning on that cash, not at $r_l$. Your hedging cost is therefore tied to $r_s$. The call costs you less to replicate, so you can sell it for less. The same reasoning says you can pay more for a put.

| Trade | Delta of the trade | Hedge | Rate on the marginal share |
|---|---|---|---|
| Sell a call | negative | buy stock | covers a short: uses $r_s$ if you are short |
| Buy a put | negative | buy stock | covers a short: uses $r_s$ if you are short |
| Buy a call | positive | sell stock | short sale if you hold no stock: $r_s$; selling owned stock: $r_l$ |
| Sell a put | positive | sell stock | same as buying a call |

That is the book's sentence: a trader carrying short stock "ought to be willing to sell calls at a lower price or buy puts at a higher price."

## The book's rule
> Whenever possible a trader should avoid a short stock position.

As a corollary, many active option traders keep some **long stock** in their position. Then when a hedge requires selling stock, they sell stock they own (a long sale, always at the ordinary rate) instead of shorting it. This avoids three complications:
- two interest rates, and so two values for every option;
- borrowing costs, and the stock may be hard to borrow;
- regulatory restrictions on short sales.

## Worked example
$C - P$ for a strike $K = 68$ using the two forwards above, with $1 + rt = 1 + 0.06 \times 8/12 = 1.04$:

| Hedger | $F$ | $C - P \approx (F - K)/1.04$ |
|---|---|---|
| Long stock | 69.02 | 0.98 |
| Short stock | 68.13 | 0.12 |

The gap is 0.86. If the call has delta about 0.55, the call is worth about $0.55 \times 0.86 \approx 0.47$ less and the put about $0.45 \times 0.86 \approx 0.39$ more to the short-stock trader. (Illustration of the idea; real values depend on the full model.)

## Common confusions
- **It is a small effect.** It matters to professional market makers who carry large positions, not to a retail trader.
- **It is not a different payoff.** The option pays the same to everyone. Only the cost of hedging it differs.
- **"Short stock position" means the trader's stock hedge or inventory, not the option.** The options themselves may be long or short.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/interest-rates-dividends-and-option-values]]
- Next: [[concepts/07-risk-measurement-i/synthetic-forward-and-put-call-parity]]
- See also: [[concepts/02-forward-pricing/arbitrage-and-cash-and-carry]], [[glossary]], [[formulas]]
