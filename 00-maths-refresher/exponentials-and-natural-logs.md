# Exponentials and natural logarithms ($e^x$ and $\ln x$)

**One-line summary:** $e^x$ is what 1 grows to when it compounds continuously at rate $x$ for one year; $\ln x$ is its undo button.

Used in: [[concepts/06-volatility/lognormal-distributions]], [[concepts/06-volatility/realized-volatility]], [[chapters/06-volatility]]

## Intuition
Compounding more often earns slightly more. Put 1 in the bank at 100% a year:

| Compounded | Result after a year |
|---|---|
| once | $(1 + 1)^1 = 2.000$ |
| twice | $(1 + 1/2)^2 = 2.250$ |
| monthly | $(1 + 1/12)^{12} = 2.613$ |
| daily | $(1 + 1/365)^{365} = 2.715$ |
| continuously | $e = 2.71828\ldots$ |

It does not grow forever: it approaches a limit, the number $e \approx 2.71828$. With a rate $r$ (not 100%) the limit is $e^{r}$.

## The maths
**Exponential.** Compounding $n$ times a year at rate $r$ for one year, as $n$ grows without limit:

$$\left(1 + \frac{r}{n}\right)^{n} \;\longrightarrow\; e^{r}$$

For $t$ years: $e^{rt}$. Also written $\exp(rt)$.

**Natural logarithm.** $\ln$ undoes $e^{\,\cdot}$:

$$\ln(e^{x}) = x \qquad e^{\ln x} = x$$

**Rules you need:**

| Rule | Example |
|---|---|
| $e^{a+b} = e^a \times e^b$ | $e^{0.1+0.2} = e^{0.1} e^{0.2}$ |
| $e^{-x} = 1/e^{x}$ | $e^{-0.12} = 1/1.1275 = 0.8869$ |
| $\ln(a/b) = \ln a - \ln b$ | $\ln(45.98/45) = \ln 45.98 - \ln 45$ |
| $\ln(1 + x) \approx x$ for small $x$ | $\ln(1.02) = 0.0198 \approx 0.02$ |

**Log return.** The continuously compounded return between prices $P_0$ and $P_1$ is

$$u = \ln\!\left(\frac{P_1}{P_0}\right) \qquad\text{and}\qquad P_1 = P_0\, e^{u}$$

Log returns **add** over time (the log of a product is the sum of the logs), which is why they are convenient. For small price changes they are almost the same as the simple percent change.

## Worked examples
**1. Continuous compounding (the book).** 1,000 at 12% for a year:
- $e^{0.12} = 1.12750$, so $1000 \times 1.1275 = 1127.50$.
- At $-12\%$: $e^{-0.12} = 0.88692$, so $1000 \times 0.88692 = 886.92$.
- Gain is $127.50$, loss is only $113.08$: ups are bigger than downs for the same rate, and the value can never reach zero.

**2. A log return.** Price goes from 45.00 to 45.98.
- Simple change: $0.98/45 = 2.178\%$.
- Log return: $\ln(45.98/45) = \ln(1.021778) = 0.02154 = 2.154\%$.
- Close, because the move is small.

**3. Log returns add.** 45 to 45.98 to 45.33: $\ln(45.98/45) + \ln(45.33/45.98) = 0.02154 - 0.01424 = 0.00730$, and $\ln(45.33/45) = 0.00730$. ✓

## Common confusions
- **$\ln$ is not "log base 10".** Natural log uses $e$.
- **$e^{-x}$ is positive.** It shrinks towards zero but never reaches it.
- **Simple vs continuous interest.** Chapters 2 and 5 used simple interest ($1 + rt$). Models often use $e^{rt}$; for short times they are nearly equal ($e^{0.02} = 1.0202$ vs $1.02$).

## Related
- Index: [[00-maths-refresher/README|Maths refresher]]
- Before: [[00-maths-refresher/simple-interest-and-time-fractions]], [[00-maths-refresher/present-value-and-discounting]]
