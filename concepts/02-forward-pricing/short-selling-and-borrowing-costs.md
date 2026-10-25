# Short selling, the short-stock rebate and the no-arbitrage band

**One-line definition:** to sell stock you do not own, you must first borrow it. The lender keeps part of the interest on your sale proceeds, so a short seller earns a *lower* rate than an ordinary lender. This opens a *range* of forward prices in which no arbitrage is possible.

## Intuition
Selling stock short means selling stock you have borrowed, hoping to buy it back cheaper later. The buyer does not care: as far as they are concerned they own the stock.

You still owe the lender the shares back, so the lender holds the sale proceeds as security. That cash technically belongs to you, so you earn interest on it, but the lender takes a cut for lending you the shares. The harder the stock is to borrow, the bigger the cut. In the extreme, you may earn *no* interest. You also have to pay the lender any dividends the stock pays while you are short.

## The maths
- Long rate $r_l$: the ordinary rate for borrowing and lending cash.
- Short rate $r_s$: the rate you earn on the cash from a short sale. Also called the **short-stock rebate**.
- Borrowing cost $r_{bc}$: the difference.

$$r_{bc} = r_l - r_s$$

The forward-price formula is the same as before, but which rate you plug in depends on the direction of the trade:

$$F_{\text{upper}} = S(1 + r_l t) - D \qquad F_{\text{lower}} = S(1 + r_s t) - D$$

If the market's forward price lies *between* $F_{\text{lower}}$ and $F_{\text{upper}}$, a trader who has to short stock cannot profit.

## Worked example (the book's numbers)
$S = 67.00$, $t = 8/12$, $D = 0.66$, long rate $r_l = 6\%$. The lender keeps 2%, so $r_s = 4\%$, $r_{bc} = 2\%$.

**Upper edge (long rate):** $67.00 \times (1 + 0.06 \times 8/12) - 0.66 = 69.68 - 0.66 = 69.02$

**Lower edge (short rate):** $67.00 \times (1 + 0.04 \times 8/12) - 0.66 = 68.7867 - 0.66 = 68.13$

Now test a market forward price of **68.75**. That is below 69.02, which looks cheap: buy the forward, sell the stock.

| Trader | Result | Calculation |
|---|---|---|
| Already **owns** the stock (sells it, earns the full 6%) | **+0.27** | $69.02 - 68.75$ |
| Does **not** own it (must short, earns only 4%) | **-0.62** | $68.13 - 68.75$ |

Check the second one cash-flow by cash-flow: sell the stock at 67.00, earn $67.00 \times 0.04 \times 8/12 = 1.79$ interest, pay the dividend $0.66$, buy the forward at $68.75$. Total: $67.00 + 1.79 - 0.66 - 68.75 = -0.62$. A loss.

**Conclusion:** a trader who does not hold stock can only profit if the forward price is **below 68.13** (reverse trade) or **above 69.02** (cash-and-carry). Anywhere in between, no arbitrage is possible.

## Which interest rate applies to options?
A stock is a deliverable security that has to be borrowed to be sold short. An **option** is a contract created between buyer and seller. You do not borrow an option to sell it. So for the cash flow from buying or selling an option, always use the ordinary **long rate**.

## Common confusions
- The band exists because of *borrowing costs*. With easy-to-borrow stock the band is narrow. With hard-to-borrow stock it widens.
- A short-stock squeeze (very hard to borrow) is the extreme case, where the rebate can be zero.
- Short sellers *pay* dividends, which is why the formula still subtracts $D$.

## Related
- Chapter: [[chapters/02-forward-pricing]]
- See also: [[concepts/02-forward-pricing/arbitrage-and-cash-and-carry]], [[concepts/02-forward-pricing/stock-dividends-and-key-dates]], [[glossary]]
