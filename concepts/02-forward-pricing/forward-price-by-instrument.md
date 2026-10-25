# Forward price formulas by instrument (commodity, stock, bond, currency)

**One-line definition:** the same "cash + costs - benefits" idea ([[concepts/02-forward-pricing/forward-price-cost-and-benefit]]) written out for each kind of underlying, because each has different costs and benefits.

## Intuition
Whatever you buy now, you pay interest on the price. What changes between instruments is the rest:

| Instrument | Costs of buying now | Benefits of buying now |
|---|---|---|
| Physical commodity (grain, oil, metals) | Interest on cash price, storage, insurance | Convenience yield (see [[concepts/02-forward-pricing/contango-backwardation-convenience-yield]]) |
| Stock | Interest on stock price | Dividends, plus interest on dividends |
| Bond or note | Interest on bond price | Coupons, plus interest on coupons |
| Foreign currency | Interest cost of borrowing the home currency | Interest earned on the foreign currency |

Notation used throughout: $t$ = time to maturity in years, $r$ = interest rate per year (a decimal). All formulas use simple interest, $(1 + rt)$.

## 1. Physical commodity

$$F = C \times (1 + r t) + (s \times t) + (i \times t)$$

- $F$ = forward price, $C$ = cash price of one unit (Natenberg uses capital $C$ *only in this chapter*; later $C$ means a call option).
- $s$ = storage cost per unit per year, $i$ = insurance cost per unit per year.
- Reading it: pay the price plus interest on it, plus storage and insurance for the time $t$.

**Example (solving for $C$).** Three-month forward $F = 77.40$, $r = 8\%$, $s = 3.00$, $i = 0.60$, $t = 3/12 = 0.25$. Rearranging (see [[00-maths-refresher/rearranging-formulas]]):

$$C = \frac{F - (s + i) \times t}{1 + r t} = \frac{77.40 - 3.60 \times 0.25}{1 + 0.08 \times 0.25} = \frac{77.40 - 0.90}{1.02} = \frac{76.50}{1.02} = 75.00$$

Check by going forwards: $75.00 \times 1.02 + 0.90 = 76.50 + 0.90 = 77.40$.

## 2. Stock

Exact version, with interest earned on each dividend:

$$F = S \times (1 + r t) - \sum_n d_n \times (1 + r_n t_n)$$

- $S$ = stock price today.
- $d_n$ = the $n$-th dividend expected before maturity.
- $t_n$ = time from that dividend's payment to maturity, $r_n$ = the interest rate that applies over that stretch (a *forward rate*, see below).
- Reading it: the stock costs $S$ plus interest, but you are paid each dividend plus the interest it earns until maturity, so subtract those.

**Example.** $S = 67.00$, $t = 8$ months, $r = 6.00\%$. Semiannual dividend $d = 0.33$, next one in 1 month (so the second is at month 7).

- $t_1 = 8 - 1 = 7$ months, $t_2 = 8 - 1 - 6 = 1$ month. Rates $r_1 = 6.20\%$, $r_2 = 6.50\%$.
- Stock with interest: $67.00 \times (1 + 0.06 \times 8/12) = 67.00 \times 1.04 = 69.68$
- First dividend with interest: $0.33 \times (1 + 0.062 \times 7/12) = 0.3419$
- Second dividend with interest: $0.33 \times (1 + 0.065 \times 1/12) = 0.3318$
- $F = 69.68 - 0.3419 - 0.3318 = 69.0063$

**Simplified version** (what the book uses from here on): add up all dividends into one number $D$ and ignore interest on them:

$$F = S \times (1 + r t) - D$$

For the same stock, $D = 2 \times 0.33 = 0.66$ and $F = 69.68 - 0.66 = 69.02$. The two answers differ by only about 1.4 cents, which is why the simplification is fine unless a dividend falls close to maturity (see [[concepts/02-forward-pricing/stock-dividends-and-key-dates]]).

**What is a forward rate?** The interest rate that applies *starting at some future date* for a stated length of time. A "$1 \times 5$" forward rate is a four-month rate that begins in one month. A "$3 \times 9$" rate is a six-month rate beginning in three months. A **forward-rate agreement (FRA)** locks in such a rate today.

## 3. Bonds and notes
Treat coupons like dividends:

$$F = B \times (1 + r t) - \sum_n c_n \times (1 + r_n t_n)$$

- $B$ = bond price, $c_n$ = $n$-th coupon, other symbols as for stocks.

**Example.** $B = 109.76$, $t = 10$ months, $r = 8.00\%$. Semiannual coupon $5.25$, next in 2 months, so $t_1 = 8$ months and $t_2 = 2$ months, with $r_1 = 8.20\%$, $r_2 = 8.50\%$.

- Bond with interest: $109.76 \times (1 + 0.08 \times 10/12) = 117.0773$
- First coupon: $5.25 \times (1 + 0.082 \times 8/12) = 5.5370$
- Second coupon: $5.25 \times (1 + 0.085 \times 2/12) = 5.3244$
- $F = 117.0773 - 5.5370 - 5.3244 = 106.2159$ (the book's figure; 106.2160 if you do not round the pieces first)

## 4. Foreign currency
A currency forward involves **two** interest rates: the rate $r_d$ on the *domestic* currency (the one you pay with) and the rate $r_f$ on the *foreign* currency (the one you buy and hold).

The spot exchange rate $S$ is quoted as "domestic units per one foreign unit", for example $S = 1.50$ means one euro costs 1.50 dollars.

$$F = S \times \frac{1 + r_d \, t}{1 + r_f \, t}$$

**Why this formula (no-arbitrage reasoning).** Start with $C_f$ units of foreign currency, worth $C_d = S \times C_f$ in domestic units today.

1. Borrow $C_d$ domestic currency. At maturity you owe $C_d (1 + r_d t)$.
2. Use it to buy $C_f$ foreign units and deposit them at $r_f$. At maturity you hold $C_f (1 + r_f t)$ foreign units.
3. Sell those foreign units forward at $F$ (domestic per foreign). At maturity you receive $F \times C_f (1 + r_f t)$ domestic units.
4. If $F$ is fair, steps 1 and 3 cancel exactly (no profit, no loss): $F \times C_f (1 + r_f t) = C_d (1 + r_d t)$.
5. Divide both sides by $C_f(1 + r_f t)$ and use $C_d / C_f = S$ to get the formula above.

**Example.** €1.00 = \$1.50. Dollar rate $r_d = 6\%$, euro rate $r_f = 4\%$, six months ($t = 0.5$):

$$F = 1.50 \times \frac{1 + 0.06 \times 0.5}{1 + 0.04 \times 0.5} = 1.50 \times \frac{1.03}{1.02} = 1.5147$$

(The PDF text of the book prints the numerator as "1.30", which is a typo for 1.03. The answer 1.5147 only works with 1.03.)

**Rule of thumb:** the currency with the *higher* interest rate trades at a forward *discount*, and the lower-rate currency at a forward *premium*. Here the euro (4%) is the lower-rate currency, so its forward price (1.5147) is above spot (1.50).

## 5. Futures and futures options
A futures contract *is* a forward contract. So the forward price for a futures contract is simply **the futures price**. A three-month future trading at \$75.00 means the three-month forward price is \$75.00. No calculation is needed, which makes futures options a little easier to evaluate than stock options. For exchange-traded options on commodities, bonds and currencies, the underlying is almost always the *futures* contract.

## Common confusions
- **Units must match.** If you add interest to a spot exchange rate you get nonsense unless both currencies' interest rates are included as a *ratio*.
- **Simple interest is an approximation.** Later chapters use continuous compounding, $e^{rt}$ in place of $1 + rt$.
- **The dividend sum is subtracted** because dividends are a *benefit* of owning stock now.

## Related
- Chapter: [[chapters/02-forward-pricing]]
- Maths needed: [[00-maths-refresher/simple-interest-and-time-fractions]], [[00-maths-refresher/summation-notation]], [[00-maths-refresher/rearranging-formulas]]
- See also: [[concepts/02-forward-pricing/forward-price-cost-and-benefit]], [[concepts/02-forward-pricing/implied-values]], [[glossary]], [[formulas]]
