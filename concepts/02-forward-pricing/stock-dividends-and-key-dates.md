# Stock dividends and the four key dates

**One-line definition:** a dividend moves through four dates: declared, ex-dividend, record, payable. Only the person who owns the stock *before the ex-date* gets the dividend.

## Intuition
Forward and option prices on a stock depend on the dividends expected before maturity ([[concepts/02-forward-pricing/forward-price-by-instrument]]). So a trader needs to estimate **how much** will be paid and **when**. The dates decide who gets paid and when the stock price drops.

## The four dates
| Date | What it means |
|---|---|
| **Declared date** | The company announces the dividend amount and the payable date. After this, the dividend is certain (until the next one), so dividend risk disappears. |
| **Ex-dividend date (ex-date)** | The first day the stock trades *without* the right to the dividend. Buy on or after this day and you do not get it. |
| **Record date** | The date you must be an official owner. Ownership becomes official on the *settlement date*, a few days after the trade. |
| **Payable date** | The day the dividend is actually paid to people who owned on the record date. |

**Timeline:** declared date → ex-date → record date → payable date.

**The book's US rules.** Settlement was three business days after the trade (T+3), so the last day to buy and still receive the dividend was three business days before the record date, and the ex-date was two business days before the record date.

**Note (out of date):** the book was written under T+3 settlement. US stock settlement has since moved to T+1 (from 28 May 2024), and with T+1 the ex-dividend date is the *same day* as the record date. The idea is unchanged: the ex-date is the cut-off, and its distance from the record date depends on the market's settlement cycle. Check your own market's rules (for example, Australia's cycle differs from the US).

## The price drop on the ex-date
On the ex-date the stock's quote is adjusted to remove the dividend.

**Example (the book's).** Stock closes at \$67.50 the day before the ex-date. Dividend is \$0.40.

- If the stock opened *unchanged in value*, it would open at $67.50 - 0.40 = 67.10$.
- It actually opens at \$68.25.
- The quote is displayed as the change against 67.10: $68.25 - 67.10 = +1.15$.
- So the screen reads **68.25, +1.15, ex-div 0.40**.

The stock *rose* \$1.15 relative to its adjusted price, even though it is only \$0.75 above yesterday's close ($68.25 - 67.50$).

## Estimating dividends
- **Amount:** use history. If a company paid \$0.25 for each of the last 10 quarters, assume \$0.25 again.
- **Date:** matters more than it looks. The simple formula $F = S(1+rt) - D$ ignores interest on dividends. That is fine unless a dividend lands close to maturity, where a slightly wrong date can noticeably change the value of the derivative.

## Common confusions
- **Ex-date vs record date.** The ex-date is the one that matters for buyers (it is the cut-off). The record date is when the company checks its list.
- **A short seller owes the dividend** to the stock lender ([[concepts/02-forward-pricing/short-selling-and-borrowing-costs]]).

## Related
- Chapter: [[chapters/02-forward-pricing]]
- See also: [[concepts/02-forward-pricing/forward-price-by-instrument]], [[glossary]]
