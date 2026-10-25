# Open Questions

Things not yet understood. Move an item to the relevant chapter note once resolved.

- [x] How are options priced from probabilities? (Chapter 5) Resolved: list prices and probabilities, take the expected option value, discount it. See [[chapters/05-theoretical-pricing-models]]
- [ ] Chapter 2 uses simple interest, $1 + rt$. Which form do later models use (continuous compounding, $e^{rt}$) and how much does it change the forward price? ([[chapters/02-forward-pricing]])
- [ ] What happens to the short-sale band when a stock is hard to borrow and the rebate is near zero? ([[chapters/02-forward-pricing]])
- [ ] Why can a European option have negative time value? ([[chapters/03-contract-specifications-and-option-terminology]], Chapter 16)
- [ ] Which exchange will I actually trade on, and what are its strikes, expiry calendar and automatic-exercise threshold? ([[chapters/03-contract-specifications-and-option-terminology]])
- [ ] Why would anyone sell an option, given limited profit and unlimited risk? ([[chapters/04-expiration-profit-and-loss]]; the book says probability decides)
- [ ] How does the "speed" of the underlying, not just its direction, affect option profits before expiration? ([[chapters/04-expiration-profit-and-loss]], Chapter 5)
- [x] How do we turn infinitely many possible prices into usable probabilities? Resolved: assume a (log)normal distribution with mean = forward price and standard deviation from volatility. [[chapters/06-volatility]]
- [x] What exactly is volatility and how is it measured? Resolved: annualized standard deviation of percent price changes; realized from history, implied from option prices. [[chapters/06-volatility]]
- [ ] Why does a riskless hedge let us ignore which way the stock goes, and how big is the hedge ratio? ([[chapters/05-theoretical-pricing-models]], Chapters 7 and 8)
- [x] Net effect of a higher interest rate on a call: forward price up (good) but present value down (bad). Which wins? Resolved: the forward-price effect, because it applies to the whole stock price while the discount applies only to the much smaller option price. [[concepts/07-risk-measurement-i/interest-rates-dividends-and-option-values]]
- [ ] How is the Black-Scholes value actually calculated from the volatility (what are $d_1$ and $d_2$)? ([[chapters/06-volatility]])
- [ ] Why does implied volatility vary across exercise prices (the "skew")? ([[chapters/06-volatility]], gold tables)
- [ ] Why do calls and puts with the same exercise price have nearly the same implied volatility? (put-call parity, Chapter 15; [[chapters/06-volatility]])
- [ ] How do volatility forecasts work, and which window should I use for historical volatility? ([[chapters/06-volatility]], later chapters)
- [x] How do the risk measures (the vega, Chapter 7) quantify which options react most to volatility? Resolved: the vega, largest near the money. [[concepts/07-risk-measurement-i/vega]]
- [ ] Where do the formulas for delta, gamma, theta, vega and rho come from? ([[chapters/07-risk-measurement-i]]; later chapters and the Black-Scholes formula)
- [ ] Why is delta only approximately the probability of finishing in the money, and which Black-Scholes number is the exact probability? ([[chapters/07-risk-measurement-i]])
- [ ] How are gamma and theta linked mathematically? ([[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]])
- [ ] How do the risk measures change as conditions change (Chapter 9), and how are they used to keep a hedge neutral (Chapter 8)? ([[chapters/07-risk-measurement-i]])
- [ ] As an individual hedging with long stock only, can I ignore the short-stock effect on option values? ([[concepts/07-risk-measurement-i/long-vs-short-stock-and-option-values]])
- [ ] (add)
