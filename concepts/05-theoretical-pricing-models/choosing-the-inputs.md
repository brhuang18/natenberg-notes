# Choosing the model inputs in practice

**One-line definition:** a model's value is only as good as its inputs. The exercise price and expiry are fixed, but the underlying price, interest rate, dividends and above all volatility all need judgement.

## 1. Exercise price
Fixed by the contract and never changes: a March 60 call cannot become a March 55 call. (An exchange may adjust it after a stock split or an extraordinary dividend, but that is bookkeeping: the contract is economically the same.)

## 2. Time to expiration
The expiry date is also fixed. But the *amount of time left* shrinks each day, and it must be entered in **years**:

$$t = \frac{\text{days to expiration}}{365}$$

Example: 60 days is $60/365 = 0.1644$ years; 30 days is $0.0822$ years. Most software does the division for you, so you just enter the days.

**Which days count?** Time is used for two jobs:
1. **Likelihood of price movement:** only *business days* matter, since prices only change when the market is open.
2. **Interest:** *every calendar day* counts, since interest accrues daily.

This looks like a conflict but is not: the model scales the business-day count for price movement to an annual number itself, so you feed in the **actual number of calendar days** and it interprets them correctly.

**Very close to expiration:** you might use hours or minutes, but discrete time steps do not perfectly match the continuous passage of time, and the inputs become less reliable. Many traders stop using model values altogether right before expiry.

## 3. Underlying price
Not always obvious: there is a bid, an ask and a last trade. The book's example: last trade 75.25, market 75.20 bid / 75.40 ask.

**Rule: use the price at which you expect to make the hedge trade.**

| You plan to... | That is a... | Hedge by... | Use a price near |
|---|---|---|---|
| Buy calls or sell puts | long market position | selling underlying | the **bid** (75.20) |
| Sell calls or buy puts | short market position | buying underlying | the **ask** (75.40) |

- Very liquid market (tight spread, lots of size): the **midpoint** ($(75.20 + 75.40)/2 = 75.30$) is usually fine for a quick decision.
- Illiquid market (wide spread, little size, fast prices): think harder; even a small order may not trade at the quoted prices.
- Nothing forces you to follow a model. But if you do, you must hedge, and the price that matters is the one you will really get on the hedge.

## 4. Interest rate
Interest enters in two ways:
1. **Forward price.** With stock-type settlement for the underlying, a higher rate raises the forward price: calls worth more, puts worth less.
2. **Present value of the option.** With stock-type option settlement, a higher rate lowers the present value of the option.

If the same rate applies to both, enter one rate. If not (e.g. foreign-currency options: foreign rate for one role, domestic rate for the other), the model needs two rates (the Garman-Kohlhagen version).

**Which rate?**
- Textbook: the **risk-free rate**, e.g. the yield on a government bill of matching maturity (a 60-day option uses a 60-day bill).
- Realistic: nobody borrows or lends at the government's rate, so traders often use a market rate such as **LIBOR** or Eurodollar futures. (The book's example is from its time; other benchmark rates are used in other markets and eras.)
- Borrowing and lending rates differ. In theory the right one depends on whether the trade is a credit (borrowing rate) or debit (lending rate).
- Interest is usually the **least important input**. A rate that "makes sense" is normally enough, except for very large or very long-dated positions.

## 5. Dividends
Only relevant for **stock options**, and only if a dividend is expected before expiry. Dividends matter because they change the forward price ([[concepts/02-forward-pricing/stock-dividends-and-key-dates]]).

- Estimate both the **amount** and the **ex-dividend date** (the first day the stock trades without the dividend). Traders focus on the ex-dividend date because you must own the stock *before* it to receive the dividend. The payment date only affects the small interest earned on it.
- Usual assumption: the company keeps its past dividend policy (e.g. 75 cents a quarter). But it can raise, cut or skip it until it is declared.
- If the ex-dividend date slips to *after* expiry, the dividend no longer counts, which for option purposes is the same as removing it. Near expiry, check the exact date.

## 6. Volatility
The hardest input to understand, and often the most important in real trading decisions. A change in assumed volatility can change an option's value dramatically, and how the market assesses volatility moves option prices too. Chapter 6.

## Summary table

| Input | Certain? | Main judgement |
|---|---|---|
| Exercise price | Yes | none |
| Time | Yes (date fixed) | enter calendar days; model handles the rest |
| Underlying price | No | bid, ask or mid? match the hedge trade |
| Interest rate | Partly | which rate? least critical input |
| Dividends (stocks) | No | amount and ex-date |
| Volatility | No | estimate; most important |

## Common confusions
- **Do not strip weekends out of the days you enter.** The model already handles business days versus calendar days.
- **Bid for long positions, ask for short positions**, because that is where the hedge trades. Mid is a shortcut, not a rule.
- **The ex-dividend date, not the payment date,** is what matters for the stock-ownership decision.

## Related
- Chapter: [[chapters/05-theoretical-pricing-models]]
- Previous: [[concepts/05-theoretical-pricing-models/riskless-hedge-and-hedge-ratio]]
- Forward price and interest: [[concepts/02-forward-pricing/forward-price-cost-and-benefit]], [[concepts/02-forward-pricing/forward-price-by-instrument]]
- Maths needed: [[00-maths-refresher/simple-interest-and-time-fractions]]
- Code: [[code/pricing_models.ipynb]] (day count and bid/ask rule at the end)
- See also: [[glossary]]
