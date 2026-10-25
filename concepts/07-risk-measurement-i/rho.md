# Rho

**One-line definition:** the rho ($P$) is the change in an option's theoretical value for each 1 percentage point change in interest rates.

## Intuition
Unlike delta, gamma, theta and vega, you cannot say "calls always have a positive rho". The sign depends on the type of underlying and how the option is settled, because rates act through two channels (the forward price and the present value, [[concepts/07-risk-measurement-i/interest-rates-dividends-and-option-values]]).

## The signs (Figure 7-2 summarized)

| Option | Rho | Reason |
|---|---|---|
| Stock call | positive | forward price rises (dominates) |
| Stock put | negative | forward price rises (hurts) and discounting (hurts) |
| Futures option, stock-type settlement | negative for calls and puts | only the discounting channel; higher rates raise the cost of carrying the option |
| Futures option, futures-type settlement | 0 | no cash changes hands, so no rate effect |
| Foreign currency option | two rhos: **rho1** (domestic rate) and **rho2** (foreign rate, sometimes called phi $\Phi$) | see [[concepts/07-risk-measurement-i/futures-and-currency-options-interest-rates]] |

## Worked example (Figure 7-13)
Call 100: rho $+0.124$, so a one-point rate rise adds about 0.124 per option. Put 100: $-0.121$. Check with a larger move: the model values a one-year at-the-money call at 12.336 with a 5% rate and 12.845 with 6%, a gain of 0.51.

Position 1 (sold 10 95 calls, long 7 underlying): $-10 \times 0.155 = -1.55$. It is negative despite owning *stock* (which has zero rho) because the long stock leg inevitably dominates the cash flow: it is financed with a debit. If rates rise, carrying that debit costs more; if they fall, less.

## Why traders mostly ignore it
The interest rate is usually the *least* important input. For that reason rho is usually less critical than delta, gamma, theta or vega, and few individual traders worry about it. A firm with a very large position should at least know its interest-rate risk. The book mostly disregards it in later examples.

## Common confusions
- **A change in rates does not change the underlying's value** from an option trader's view (footnote 10). The underlying's rho is 0 ([[concepts/07-risk-measurement-i/risk-measures-of-the-underlying-and-signs]]).
- **"Rho" and the dividend:** rho only concerns the interest rate; dividends are a separate input.

## Related
- Chapter: [[chapters/07-risk-measurement-i]]
- Previous: [[concepts/07-risk-measurement-i/vega]]
- Next: [[concepts/07-risk-measurement-i/risk-measures-of-the-underlying-and-signs]]
- See also: [[glossary]], [[formulas]]
