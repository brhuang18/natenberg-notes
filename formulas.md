# Formulas

Each formula: the equation, every symbol defined, and what it means in plain English.

## Template

$$\text{formula here}$$

- Symbols: ...
- Intuition: ...
- Source: [[chapters/chapter-template]]

---

## Chapter 1: Financial Contracts

**Notional value, physical commodity**

$$\text{notional value} = \text{units delivered} \times \text{unit price}$$

- Intuition: the size of the deal, not cash paid. Example: $1{,}000 \times \$75 = \$75{,}000$.
- Source: [[chapters/01-financial-contracts]]

**Notional value, cash-settled index**

$$\text{notional value} = \text{index price} \times \text{point value}$$

- Intuition: the exchange sets the point value so the contract is a sensible size to trade. Example: $825 \times \$200 = \$165{,}000$.
- Source: [[chapters/01-financial-contracts]]

**Futures variation**

$$\text{variation} = (P_{\text{new}} - P_{\text{old}}) \times \text{units per contract} \times \text{contracts}$$

- Symbols: $P$ is the futures price; contracts are positive for long and negative for short. Positive means credit, negative means debit.
- Intuition: the daily cash transfer that keeps the contract at its original agreed price. See [[concepts/01-financial-contracts/settlement-margin-and-variation]].
- Source: [[chapters/01-financial-contracts]]

---

## Chapter 2: Forward Pricing

Notation: $t$ = years to maturity (months / 12), $r$ = annual interest rate as a decimal.

**Forward price, general idea**

$$F = \text{cash price} + \text{costs of buying now} - \text{benefits of buying now}$$

- Intuition: owning early costs you and pays you; a forward skips both, so the price must give them back. See [[concepts/02-forward-pricing/forward-price-cost-and-benefit]].
- Source: [[chapters/02-forward-pricing]]

**Basis**

$$\text{basis} = \text{cash price} - \text{forward price}$$

- Intuition: negative in a normal (contango) market, positive in backwardation.

**Physical commodity**

$$F = C(1 + rt) + st + it$$

- Symbols: $C$ cash price per unit (capital $C$ only in this chapter), $s$ annual storage cost per unit, $i$ annual insurance cost per unit.
- Example: $C = 75.00$, $r = 8\%$, $t = 0.25$, $s = 3.00$, $i = 0.60$ gives $F = 77.40$.

**Stock (exact)**

$$F = S(1 + rt) - \sum_n d_n(1 + r_n t_n)$$

- Symbols: $S$ stock price, $d_n$ the $n$-th dividend, $t_n$ years from that dividend to maturity, $r_n$ the forward rate over that stretch.

**Stock (simplified)**

$$F = S(1 + rt) - D$$

- Symbols: $D$ = total dividends before maturity; interest on dividends ignored.
- Example: $67.00 \times 1.04 - 0.66 = 69.02$.

**Bond or note**

$$F = B(1 + rt) - \sum_n c_n(1 + r_n t_n)$$

- Symbols: $B$ bond price, $c_n$ the $n$-th coupon.

**Foreign currency**

$$F = S \times \frac{1 + r_d t}{1 + r_f t}$$

- Symbols: $S$ domestic currency per one foreign unit, $r_d$ domestic rate, $r_f$ foreign rate.
- Intuition: the forward rate that makes borrowing at home to hold the foreign currency a break-even trade.

**Implied values**

$$S = \frac{F + D}{1 + rt} \qquad r = \frac{\frac{F + D}{S} - 1}{t} \qquad D = S(1 + rt) - F$$

- Intuition: solve the stock formula for whichever input is missing. See [[concepts/02-forward-pricing/implied-values]].

**Commodity cash price implied by a forward**

$$C = \frac{F - (s + i)t}{1 + rt}$$

**Convenience yield**

$$\text{convenience yield} = \text{actual cash price} - \text{cash price implied by the forward}$$

**Short-sale band (stock)**

$$S(1 + r_s t) - D \;\le\; F \;\le\; S(1 + r_l t) - D \qquad r_{bc} = r_l - r_s$$

- Intuition: someone who must borrow stock earns only the short rate, so there is a range of forward prices with no arbitrage. See [[concepts/02-forward-pricing/short-selling-and-borrowing-costs]].

---

## Chapter 3: Contract Specifications and Option Terminology

**Call intrinsic value**

$$\max(0,\; S - X)$$

- Symbols: $S$ underlying price, $X$ exercise price.
- Intuition: buy at $X$, sell at $S$; if that loses money, do nothing, so never below 0. See [[00-maths-refresher/max-function]].
- Example: $S = 435$, $X = 400$ gives 35.
- Source: [[chapters/03-contract-specifications-and-option-terminology]]

**Put intrinsic value**

$$\max(0,\; X - S)$$

- Intuition: sell at $X$, buy back at $S$. Example: $X = 70$, $S = 62$ gives 8.

**Premium and time value**

$$\text{premium} = \text{intrinsic value} + \text{time value} \qquad \text{time value} = \text{premium} - \text{intrinsic value}$$

- Example: April 400 call at 50 with intrinsic 35 has time value 15. See [[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]].

**Exercise into the physical underlying**

$$\text{cash} = X \times \text{units} \quad (\text{call exerciser pays, put exerciser receives})$$

- Example: exercise 1 stock call at 110: pay $100 \times 110 = 11{,}000$.

**Exercise into a futures position**

$$\text{variation} = (F - X) \times \text{point value} \times \text{contracts} \quad (\text{long futures; negative contracts for short})$$

- Symbols: $F$ current futures price. Example: exercise a 80 call with $F = 85$, point value 1,000: $+5{,}000$. See [[concepts/03-contract-specifications-and-option-terminology/exercise-assignment-and-settlement]].

**Exercise into cash (index)**

$$\text{call: } (S - X) \times \text{point value} \times \text{contracts} \qquad \text{put: } (X - S) \times \text{point value} \times \text{contracts}$$

- Example: 3 March 250 calls, index 300, \$500 per point: $50 \times 500 \times 3 = 75{,}000$.

---

## Chapter 4: Expiration Profit and Loss

**P&L at expiration**

$$\text{P\&L}_{\text{long}} = \text{value at expiration} - \text{price paid} \qquad \text{P\&L}_{\text{short}} = \text{price received} - \text{value at expiration}$$

- Intuition: the parity graph slid down by a debit or up by a credit. See [[concepts/04-expiration-profit-and-loss/expiration-pnl-and-breakeven]].
- Source: [[chapters/04-expiration-profit-and-loss]]

**Breakeven, single option** (exercise price $X$, premium $p$)

$$\text{call: } S = X + p \qquad\qquad \text{put: } S = X - p$$

- Example: long 100 call at 3.50 breaks even at 103.50; 95 put at 2.25 at 92.75.

**Slope of a position graph**

$$\text{slope} = \frac{\text{change in position value}}{\text{change in underlying price}}$$

- Table: out-of-the-money option 0; long ITM call $+1$; short ITM call $-1$; long ITM put $-1$; short ITM put $+1$; long underlying $+1$; short underlying $-1$. Multiply by number of contracts and add. See [[concepts/04-expiration-profit-and-loss/slope-method-for-combined-positions]].

**Walking along a stretch**

$$y_{\text{new}} = y_{\text{old}} + m \times \Delta x$$

- Symbols: $m$ slope, $\Delta x$ change in underlying price, $y$ P&L.

**Breakeven within a stretch**

$$x_{\text{breakeven}} = x_0 - \frac{y_0}{m}$$

- Symbols: $(x_0, y_0)$ a known point on the stretch, $m$ its slope; only valid if the result lies inside the stretch. See [[00-maths-refresher/slope-and-straight-lines]] and [[concepts/04-expiration-profit-and-loss/complex-position-pnl-walkthrough]].

**Long call plus short put, same exercise price**

$$\max(0, S - X) - \max(0, X - S) = S - X$$

- Intuition: behaves like a long underlying position. See [[concepts/04-expiration-profit-and-loss/equivalent-positions]].

---

## Chapter 5: Theoretical Pricing Models

**Expected value**

$$E = \sum_{i=1}^{n} p_i\, x_i$$

- Symbols: $x_i$ possible outcomes, $p_i$ their probabilities (decimals that add to 1), $n$ number of outcomes.
- Intuition: a weighted average; likelier outcomes count more. Die: $(1+2+3+4+5+6)/6 = 3.5$. See [[00-maths-refresher/probability-and-expected-value]].
- Source: [[chapters/05-theoretical-pricing-models]]

**Expected value of a call and a put at expiration**

$$E_{\text{call}} = \sum_{i=1}^{n} p_i \max(S_i - X,\,0) \qquad E_{\text{put}} = \sum_{i=1}^{n} p_i \max(X - S_i,\,0)$$

- Symbols: $S_i$ possible underlying prices at expiration, $p_i$ their probabilities, $X$ exercise price.
- Intuition: probability of each price times the option's intrinsic value there. See [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]].

**Theoretical value, stock-type settlement**

$$\text{theoretical value} = \frac{E}{1 + r\,t}$$

- Symbols: $E$ expected value at expiration, $r$ annual interest rate (decimal), $t$ time in years.
- Intuition: the present value of the expected value. Example: $6.00/1.02 = 5.88$. See [[00-maths-refresher/present-value-and-discounting]].

**Probabilities must average to the forward price**

$$\sum_{i=1}^{n} p_i\, S_i = F \qquad F = S_{\text{today}}\,(1 + r\,t)\ \text{(stock, no dividend)}$$

- Intuition: otherwise the forward could be arbitraged against cash. Example: $100 \times 1.02 = 102$.

**Time input**

$$t = \frac{\text{days to expiration}}{365}$$

- Intuition: models use years; software usually does this division for you. See [[concepts/05-theoretical-pricing-models/choosing-the-inputs]].

**Call minus put under a distribution centred on $F$** (our derivation)

$$E_{\text{call}} - E_{\text{put}} = F - X$$

- Intuition: because $\max(S - X, 0) - \max(X - S, 0) = S - X$ at every price. Example: $5.40 - 3.40 = 102 - 100$.

---

## Chapter 6: Volatility

**Range from a mean and standard deviation**

$$\text{mean} \pm k \times \text{standard deviation}, \quad k = 1, 2, 3 \;\Rightarrow\; 68.3\%,\ 95.4\%,\ 99.7\%$$

- Intuition: how likely a value is to fall within $k$ standard deviations of the centre. See [[concepts/06-volatility/mean-and-standard-deviation]].
- Source: [[chapters/06-volatility]]

**Z-score**

$$z = \frac{x - \text{mean}}{\text{standard deviation}}$$

- Intuition: "how many standard deviations from the mean". Example: $(35 - 100)/20 = -3.25$. See [[00-maths-refresher/normal-distribution-and-z-scores]].

**One-year price range from volatility** (forward $F$, volatility $\sigma$ as a decimal)

$$F \pm k\,(\sigma F)$$

- Intuition: volatility is a percent of the forward price. Example: $F = 108$, $\sigma = 20\%$: one standard deviation $= 21.60$. See [[concepts/06-volatility/volatility-as-a-standard-deviation]].

**Volatility for a different time** ($t$ in years)

$$\sigma_t = \sigma_{\text{annual}} \sqrt{t}$$

- Intuition: random ups and downs partly cancel, so spread grows with the square root of time. Daily: divide by $\sqrt{256} = 16$. Weekly: divide by $\sqrt{52} \approx 7.2$. Example: $45 \times 0.37/16 = 1.04$. See [[concepts/06-volatility/scaling-volatility-for-time]].

**Standard deviation of a set of values** ($n - 1$ for a sample)

$$s = \sqrt{\frac{\sum_{i=1}^{n} (x_i - \bar x)^2}{n - 1}}$$

- Symbols: $x_i$ values, $\bar x$ their mean, $n$ the count. See [[00-maths-refresher/standard-deviation-and-variance]].

**Log return and realized volatility**

$$u_i = \ln\frac{P_i}{P_{i-1}} \qquad \sigma_{\text{realized}} = s(u) \times \sqrt{\text{periods per year}}$$

- Intuition: measure how jumpy the changes were, then annualize (daily data: $\times 16$). Example: five changes of a 45 stock give 27.8%. See [[concepts/06-volatility/realized-volatility]].

**Continuous compounding**

$$\left(1 + \frac{r}{n}\right)^{n} \to e^{r} \qquad \text{amount} = P\,e^{rt}$$

- Example: $1000\,e^{0.12} = 1127.50$ and $1000\,e^{-0.12} = 886.92$. See [[00-maths-refresher/exponentials-and-natural-logs]] and [[concepts/06-volatility/lognormal-distributions]].

**Rate volatility** (contracts quoted as 100 minus a rate)

$$\text{daily st. dev.} \approx (100 - \text{price}) \times \frac{\sigma}{16}$$

- Example: price 93, $\sigma = 26\%$: $7 \times 0.26/16 = 0.11$. See [[concepts/06-volatility/interest-rate-products-and-rate-volatility]].

**Implied volatility** (solved numerically)

$$\text{model}(S, X, t, r, \sigma_{\text{implied}}) = \text{option price}$$

- Intuition: the model run backwards. Example: the 105 call at 3.60 gives 28.50%. See [[concepts/06-volatility/implied-volatility]].

## Chapter 7: Risk Measurement I

**Forward price with the financing rate you actually face**

$$F = S\,(1 + r\,t) - D \qquad r = r_l \text{ (long stock)} \ \text{or} \ r = r_s = r_l - r_{bc} \text{ (short stock)}$$

- Symbols: $S$ stock price, $t$ years, $D$ dividends, $r_l$ ordinary rate, $r_s$ short rate, $r_{bc}$ borrowing cost.
- Intuition: shorting earns less interest, so the forward is lower, so calls are worth less and puts more. Example: 69.02 (long) vs 68.13 (short). See [[concepts/07-risk-measurement-i/long-vs-short-stock-and-option-values]].

**Call minus put** (simple interest preview of put-call parity)

$$C - P = \frac{F - K}{1 + r\,t}$$

- Symbols: $C, P$ call and put values, $K$ strike, $F$ forward price.
- Intuition: call plus short put pays $S_T - K$, worth the discounted $F - K$. Example: $F = 69.02$, $K = 68$, $1 + rt = 1.04$ gives 0.98. See [[concepts/07-risk-measurement-i/synthetic-forward-and-put-call-parity]].

**Delta hedge ratio and position delta**

$$\text{underlying per option} = \frac{100}{\Delta} \qquad \text{position delta} = \sum \text{quantity} \times \Delta$$

- Intuition: delta 50 calls need 1 underlying per 2 options. Delta in whole numbers. See [[concepts/07-risk-measurement-i/delta]].

**Delta after a price move** ($\Delta S = S_2 - S_1$)

$$\Delta_{\text{new}} = \Delta + \Delta S \times \Gamma$$

- Intuition: add gamma per point when the price rises, subtract when it falls. Example: $40 + 4 \times 2.5 = 50$. See [[concepts/07-risk-measurement-i/gamma]].

**New option value from delta and gamma**

$$C_{\text{new}} \approx C + \Delta S \times \Delta + \tfrac12 (\Delta S)^2 \times \Gamma$$

- Symbols: $\Delta$ and $\Gamma$ as decimals (0.40, 0.025). The book prints $S_1 - S_2$ for the change; it should be $S_2 - S_1$.
- Intuition: price change times the *average* delta. Example: $3.65 + 4 \times 0.45 = 5.45$. See [[concepts/07-risk-measurement-i/estimating-option-value-with-delta-and-gamma]].

**Estimate with theta, vega and rho**

$$\text{value change} \approx \Theta \times \text{days} + \text{vega} \times \Delta\sigma + \text{rho} \times \Delta r$$

- Intuition: each risk measure is a slope; multiply by the change. Example: vega 0.15, volatility +1 point: +0.15. See [[concepts/07-risk-measurement-i/vega]].

**Theoretical edge of a position**

$$E = \sum \text{quantity} \times (\text{theoretical value} - \text{price})$$

- Symbols: quantity $+$ for bought, $-$ for sold; the underlying has $E = 0$.
- Example: $-10$ calls at 8.55, theoretical 8.33: $-10 \times (8.33 - 8.55) = +2.20$. See [[concepts/07-risk-measurement-i/theoretical-edge]].

**Breakeven (implied) volatility of a position**

$$\sigma_{\text{breakeven}} \approx \sigma_0 - \frac{E}{\text{vega}}$$

- Symbols: $\sigma_0$ the volatility used, $E$ total edge, vega total position vega (per point).
- Example: $25 - 2.20/(-1.70) = 26.29\%$. See [[concepts/07-risk-measurement-i/breakeven-volatility-of-a-position]].

**Black-Scholes relation between theta and gamma** (pointer; stock, no dividend, theta per year)

$$\Theta + r\,S\,\Delta + \tfrac12\,\sigma^2 S^2\,\Gamma = r\,V$$

- Intuition: time decay mostly pays for curvature. See [[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]].

## Chapter 8: Dynamic Hedging

**Total delta position and the adjustment** (whole-number deltas; $+$ long or bought, $-$ short or sold)

$$\text{total delta} = \sum (\text{quantity} \times \Delta) \qquad \text{contracts to sell} = \frac{\text{total delta}}{100}$$

- Symbols: quantity in contracts; the underlying has $\Delta = 100$; a negative result means buy.
- Intuition: the trade has the opposite sign of the imbalance. Example: 100 calls at delta 54 and 50 short: $5{,}400 - 5{,}000 = +400$, sell 4. See [[concepts/08-dynamic-hedging/delta-neutral-adjustments]].

**Interest on a cash flow** (simple interest)

$$\text{interest} = \text{cash} \times r \times \frac{\text{days left}}{365}$$

- Symbols: $r$ annual rate as a decimal; cash $+$ received, $-$ paid; days left to expiration.
- Intuition: credits earn, debits cost. Example: $+398.00 \times 0.06 \times 63/365 = +4.12$. See [[concepts/08-dynamic-hedging/hedge-pnl-components-and-discounting]].

**Total hedge result, discounted**

$$\text{P\&L today} = \frac{\text{original hedge} + \text{adjustments} + \text{carry} + \text{interest items}}{1 + r \times \frac{\text{days}}{365}}$$

- Example: $-422.50 + 467.55 - 5.75 + 56.21 - 5.27 = 90.24$, then $90.24 / (1 + 0.06 \times 70/365) = 89.21$.

**Predicted P&L of the hedge**

$$\text{predicted} = \text{options} \times (\text{theoretical value} - \text{price paid}) \quad (\text{reverse the sign if sold})$$

- Example: $100 \times (5.89 - 5.00) = +89.00$; sold puts: $100 \times (1.70 - 1.46) = +24.00$. See [[concepts/08-dynamic-hedging/stock-option-hedge-walkthrough]].

**Variation on a futures position**

$$\text{variation} = \text{number short} \times (\text{old price} - \text{new price})$$

- Intuition: a short position gains when the price falls. Example: $42 \times (60.83 - 62.78) = -81.90$. See [[concepts/08-dynamic-hedging/futures-option-hedge-and-variation]].

**Unhedged amount** (our link to Chapter 7; not printed in this chapter)

$$\text{unhedged amount} \approx \tfrac12\,\Gamma\,(\Delta S)^2 \qquad \text{hedged P\&L per interval} \approx \tfrac12\,\Gamma\,(\Delta S)^2 + \Theta \times \text{days}$$

- Symbols: $\Gamma$ gamma (decimal, per point), $\Delta S$ the price move, $\Theta$ theta per day (negative for a long option); interest ignored.
- Intuition: curvature pays for movement, theta charges for waiting. Example: $\tfrac12 \times 0.0248 \times 1.80^2 = 0.040$. See [[concepts/08-dynamic-hedging/gamma-and-the-unhedged-amount]].

**Breakeven volatility of the hedge**

$$\sigma_{\text{breakeven}} = \text{implied volatility of the option at the price paid}$$

- Intuition: realized volatility above it: profit; below it: loss. Example: the 5.00 call has implied volatility 32.40%. See [[concepts/08-dynamic-hedging/realized-volatility-and-the-race]].

**Replication principle**

$$\text{theoretical value} = \text{present value of the sum of the dynamic hedge's cash flows}$$

- Example: $89.21 + 500.00 = 589.21 \approx 100 \times 5.89$. See [[concepts/08-dynamic-hedging/option-replication-and-the-hedging-principle]].

