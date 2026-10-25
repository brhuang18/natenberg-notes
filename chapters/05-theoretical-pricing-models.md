# Chapter 5: Theoretical Pricing Models

## Summary
Owning an option is not like owning the underlying. A stock buyer only needs the price to go the right way; an option buyer also needs it to get there **fast enough**, before time runs out. Because the future is uncertain, an option's fair price (its **theoretical value**) is built from probabilities: list the prices the underlying might have at expiration, give each a probability, work out the option's **expected value**, and discount it for interest. The probabilities must be set so the underlying's average outcome equals its **forward price**. The **Black-Scholes model** is the practical version of this idea: it needs five inputs (exercise price, time, underlying price, interest rate, volatility) and comes with a **riskless hedge** in the underlying, which is how a trader captures a mispricing. A model is a tool with limits, "garbage in, garbage out", so managing risk matters as much as calculating the value.

## Key concepts
- **Direction vs speed** - an option buyer must be right about *where* and *how fast*; many option strategies depend only on speed. [[concepts/05-theoretical-pricing-models/direction-and-speed]]
- **Expected value** - the long-run average payout, found by multiplying each outcome by its probability and adding. [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]
- **Edge** - the gap between the price of a bet and its expected value; the profit (in the long run) of whoever is on the right side.
- **Theoretical value** - the price at which you just break even in the long run: the *present value of the expected value*.
- **Long run vs short run** - an edge only pays off if you survive bad luck long enough, which is why risk management matters. [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]
- **Model** - a simplified picture of the world that depends on assumptions and inputs. [[concepts/05-theoretical-pricing-models/models-and-their-limits]]
- **Simple approach (four steps)** - prices, probabilities, expected option value, discount. [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]]
- **Forward price as the mean** - if the underlying market is arbitrage-free, the probabilities must average out to the forward price. [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]]
- **At the money vs at the forward** - exercise price equals the current price / equals the forward price. At-the-forward options are often the benchmark.
- **Black-Scholes model** (with the Black and Garman-Kohlhagen variants) - the standard pricing model; the variants differ only in how they find the forward price and the settlement. [[concepts/05-theoretical-pricing-models/black-scholes-model-and-inputs]]
- **Riskless hedge / hedge ratio** - the opposite underlying position that cancels small price moves in an option position. [[concepts/05-theoretical-pricing-models/riskless-hedge-and-hedge-ratio]]
- **Model inputs in practice** - which price, how to measure time, which interest rate, what to do about dividends. [[concepts/05-theoretical-pricing-models/choosing-the-inputs]]

## Formulas
**Expected value of a quantity** with outcomes $x_i$ and probabilities $p_i$ (the $p_i$ add up to 1)

$$E = \sum_{i=1}^{n} p_i \, x_i$$

**Expected value of a call and a put at expiration** ($S_i$ = possible underlying prices, $X$ = exercise price)

$$E_{\text{call}} = \sum_{i=1}^{n} p_i \,\max(S_i - X,\, 0) \qquad E_{\text{put}} = \sum_{i=1}^{n} p_i \,\max(X - S_i,\, 0)$$

**Theoretical value with stock-type settlement** (present value of the expected value; simple interest $r$ per year for $t$ years)

$$\text{theoretical value} = \frac{E}{1 + r\,t}$$

**No-arbitrage condition on the probabilities** (the average underlying price must be the forward price $F$)

$$\sum_{i=1}^{n} p_i\, S_i = F$$

**Time input to the model** (one year is the unit)

$$t = \frac{\text{days to expiration}}{365}$$

Symbols and intuition for each are in [[formulas]].

## Worked example
Stock at 100, interest 12% a year, option expires in 2 months, no dividend, stock-type settlement. A **100 call**.

Growth factor: $1 + 0.12 \times \tfrac{2}{12} = 1.02$. Forward price: $100 \times 1.02 = 102$.

| Distribution (prices with probabilities) | Mean | Expected value of the 100 call | Theoretical value (divide by 1.02) |
|---|---|---|---|
| Fig 5-2: 80, 90, 100, 110, 120, each 20% | 100 | $0.2(0) + 0.2(0) + 0.2(0) + 0.2(10) + 0.2(20) = 6.00$ | $6.00 / 1.02 = 5.88$ |
| Fig 5-3: same prices; 10%, 20%, 40%, 20%, 10% | 100 | $0.2(10) + 0.1(20) = 4.00$ | $4.00 / 1.02 = 3.92$ |
| Fig 5-4: 82, 92, 102, 112, 122 with 10%, 20%, 40%, 20%, 10% | 102 | $0.4(2) + 0.2(12) + 0.1(22) = 5.40$ | $5.40 / 1.02 = 5.29$ |
| Fig 5-5: 83, 90, 99, 110, 123 with 6%, 15%, 39%, 33%, 7% | 102 | $0.33(10) + 0.07(23) = 4.91$ | $4.91 / 1.02 = 4.81$ |

Only the last two have the right mean (the forward price, 102). Reading across the rows:
- Squeezing the probabilities towards 100 (row 1 to row 2) cut the call's value from 6.00 to 4.00 without moving the mean. How *spread out* the outcomes are matters, which is what **volatility** (Chapter 6) measures.
- Shifting the distribution up by 2 (row 2 to row 3) raised the value from 4.00 to 5.40: a higher forward price helps a call.

Our own check: for the Fig 5-4 distribution the put has expected value $0.1(18) + 0.2(8) = 3.40$, and call minus put $= 5.40 - 3.40 = 2.00 = F - X = 102 - 100$.

![The four distributions and the 100 call's payoff](../images/ch05-probability-distributions.png)

![Same mean, wider spread: bigger call value](../images/ch05-spread-and-call-value.png)

Also from the chapter: a die pays its face value, so the expected payout is $(1+2+3+4+5+6)/6 = 3.5$. A roulette bet on one number pays 36 if it wins and has 38 slots, so its expected value is $36/38 = 0.9474$; sold for 1.00, the casino's edge is about 5 cents. If the winnings arrive in two months at 12% interest, the break-even price is $0.95 / 1.02 \approx 0.93$.

Everything is recomputed in [[code/pricing_models.ipynb]].

## Concepts explained in detail
- [[concepts/05-theoretical-pricing-models/direction-and-speed]]
- [[concepts/05-theoretical-pricing-models/expected-value-and-theoretical-value]]
- [[concepts/05-theoretical-pricing-models/models-and-their-limits]]
- [[concepts/05-theoretical-pricing-models/pricing-an-option-from-probabilities]]
- [[concepts/05-theoretical-pricing-models/black-scholes-model-and-inputs]]
- [[concepts/05-theoretical-pricing-models/riskless-hedge-and-hedge-ratio]]
- [[concepts/05-theoretical-pricing-models/choosing-the-inputs]]

## Maths I needed to recall
- [[00-maths-refresher/probability-and-expected-value]] - probabilities, weighted averages, "expected" does not mean "will happen"
- [[00-maths-refresher/present-value-and-discounting]] - dividing by $1 + rt$ to bring a future amount to today
- [[00-maths-refresher/summation-notation]] - the $\sum$ in the expected-value formulas (from Chapter 2)
- [[00-maths-refresher/max-function]] - the $\max(S - X, 0)$ payoff (from Chapter 3)
- [[00-maths-refresher/simple-interest-and-time-fractions]] - the growth factor $1 + rt$ (from Chapter 2)

## Code
- [[code/pricing_models.ipynb]] - expected value and theoretical value for any list of (price, probability) pairs; reproduces the book's examples; shows how spread changes a call's value; draws the figures

## Notes on the book's text
- The text for Figure 5-3 prints the probabilities as "(0% x 0) + (20% x 0) + (0% x 0) + (20% x $10) + (10% x $20)". The figure itself (and the answer of 4.00) uses 10%, 20%, 40%, 20%, 10%.
- In the underlying-price section the book writes "72.25, the last trade price"; the example's last trade is 75.25.
- The Dividends section refers to "Figure 5-5" for the list of inputs; the inputs figure is Figure 5-6.
- The "5 cents of edge" is rounded: $1.00 - 36/38 = 0.0526$.

## Open questions
- [ ] How do we turn the infinite possible prices into a usable set of probabilities? (The book says Chapter 6: the normal distribution and volatility)
- [ ] What exactly is *volatility* and how is it measured? (Chapter 6)
- [ ] Why does a riskless hedge let us ignore the probability that the stock goes up, and how many underlying contracts is the hedge ratio? (Chapter 7 on the delta, Chapter 8 on dynamic hedging)
- [ ] Net effect of a higher interest rate on a call: the forward price rises (good for calls) while the present value falls (bad for calls). Which wins, and by how much? (Chapter 7 covers the rho, the interest-rate sensitivity)
- [ ] How do you price an option that can be exercised early (American)? (Chapter 16)
