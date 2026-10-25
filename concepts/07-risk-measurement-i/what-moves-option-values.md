# What moves option values: the basic directions

**One-line definition:** an option's value responds to the underlying price, volatility, time and (a little) interest rates and dividends, and the *direction* of each response is the same for every option of a given type.

## Intuition
Owning a stock has one worry: which way does the price go? An option has several worries at once, because several inputs feed the pricing model ([[concepts/05-theoretical-pricing-models/black-scholes-model-and-inputs]]). If any input is estimated wrongly, or changes later, the option's value changes. Much of an option trader's education is learning *which way* and *how much* each input pushes the value.

This note covers the **which way**. The risk measures (delta, gamma, theta, vega, rho) cover the **how much**.

## The directions (Figure 7-1)

| If... | Call values will... | Put values will... |
|---|---|---|
| The underlying price rises | rise | fall |
| The underlying price falls | fall | rise |
| Volatility rises | rise | rise |
| Volatility falls | fall | fall |
| Time passes | fall* | fall* |

*In some unusual cases an option can rise in value as time passes, with everything else unchanged. See [[concepts/07-risk-measurement-i/theta]].

Why each one makes sense:
- **Underlying up helps calls.** A call is the right to buy; a higher stock price means a bigger gap to the exercise price. A put is the opposite.
- **Volatility up helps both.** A wider spread of possible prices ([[concepts/06-volatility/volatility-and-option-values]]) puts more probability in the region beyond the exercise price, where an option pays off, while the downside is limited to the premium.
- **Time passing hurts both.** Less time means less chance of a large move, so less time value ([[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]]).
- **Interest rates and dividends** are the awkward ones: they act through the forward price. See [[concepts/07-risk-measurement-i/interest-rates-dividends-and-option-values]].

## From direction to the five risk measures

| Question | Risk measure | Positive means... |
|---|---|---|
| How much does value change per 1 point of underlying? | delta | you want the underlying to rise |
| How fast does the delta itself change? | gamma | you want big, fast moves |
| How much value is lost per day? | theta | time helps you (negative: hurts) |
| How much per 1 volatility point? | vega | you want implied volatility to rise |
| How much per 1 interest-rate point? | rho | you want rates to rise |

This is the book's Figure 7-15. See [[concepts/07-risk-measurement-i/risk-measures-of-the-underlying-and-signs]] for the signs for each position type.

## Common confusions
- **"Time passes fall" has an exception.** It is rare (deep in the money, European, stock-type settlement). Treat it as true unless told otherwise.
- **Volatility up helps puts too.** Many beginners think rising volatility is "bad news, so bad for calls". The model only cares about the spread of prices, not their direction.
- **These are all "everything else unchanged".** In real markets inputs move together (the price falls and implied volatility jumps), so a single direction rule can mislead.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- See also: [[glossary]], [[formulas]]
