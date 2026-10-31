# Short-dated at-the-money options: the riskiest options

**One-line definition:** at-the-money options close to expiration, in a low-volatility market, have the largest gamma (and theta) of all options: their deltas can swing from near 0 to near 100 with only a small move in the underlying.

## Intuition
This is the chapter's punch line. Put together three results:
1. Gamma is greatest at the money ([[concepts/09-risk-measurement-ii/gamma-in-different-conditions]]).
2. At-the-money gamma **rises** as time passes and as volatility falls.
3. Delta moves away from 50 as time passes or volatility falls ([[concepts/09-risk-measurement-ii/delta-changes-with-volatility-and-time]]).

So an at-the-money option starts with a delta of about 50 and looks calm. But it is sitting on a knife edge: the chance of finishing in the money is decided by a tiny move, and the delta races toward 0 or 100 as soon as the underlying moves. The book calls these "gamma options": "Although these gamma options initially have delta values close to 50, their deltas can change dramatically with only small moves in the price of the underlying contract, moving very quickly toward 0 or 100."

## The maths
Delta of an at-the-money 100 call as the underlying moves (strike 100, no interest, [[code/risk_measures_ii.ipynb]]):

| Case | Underlying 98 | 99 | 100 | 101 | 102 | Gamma at 100 |
|---|---|---|---|---|---|---|
| 91 days, volatility 25% | 46.0 | 49.3 | 52.5 | 55.7 | 58.7 | 3.2 |
| 30 days, volatility 25% | 40.3 | 45.8 | 51.4 | 56.9 | 62.3 | 5.6 |
| 3 days, volatility 15% | 7.0 | 23.2 | 50.3 | 77.0 | 92.8 | 29.3 |
| 1 day, volatility 15% | 0.5 | 10.1 | 50.2 | 89.8 | 99.4 | 50.8 |

In the first row a 4-point range moves delta from 46 to 59: the option is "about 50" throughout. In the last row a **2-point range moves delta from 0.5 to 99.4**: the option flips from "worthless" to "the underlying itself".

The same options also have the biggest theta (an at-the-money option's decay accelerates toward expiration, [[concepts/09-risk-measurement-ii/theta-in-different-conditions]]): with 3 days left and volatility 15% the call is worth 0.54 and loses about 0.09 a day, a sixth of its value every day.

## Worked example: a short position and one wiggle
You sell 100 of the 3-day, 100 calls (volatility 15%, underlying 100) and hedge to delta neutral by buying 50.3 underlying contracts ($100 \times 50.3 = 5{,}030$ deltas). You collect time decay of about $100 \times 0.09 = 9$ per day.

The underlying rises 1 point to 101, where the call delta is 77.0:
1. Options: $-100 \times 77.0 = -7{,}700$ deltas. Underlying: $+5{,}030$. Total $-2{,}670$: you are short.
2. Rehedge by **buying** 26.7 contracts at 101.

The underlying falls back to 100, where the call delta is again 50.3:
3. Options: $-5{,}030$. Underlying: $5{,}030 + 2{,}670 = 7{,}700$. Total $+2{,}670$: you are long.
4. Rehedge by **selling** 26.7 contracts at 100.

The last two trades bought at 101 and sold at 100: a loss of $26.7 \times 1 = 26.7$. One one-point wiggle and back cost about **three days of time decay**, and this was a sedate wiggle. This is the cost of being short gamma: [[concepts/08-dynamic-hedging/gamma-and-the-unhedged-amount]] (and the mirror image: a long position collects it, but pays the decay).

## Common confusions
- **"Short-dated" is not "low risk".** Small premium and small vega do not mean small risk: the risk is in delta.
- **Both sides can lose.** Gamma helps the buyer who is right about the speed of the market, but a buyer pays the theta every day the market sits still. Neither long nor short is "safe".
- **This is a feature of the model with a quiet market.** In a high-volatility market, the same option is much less jumpy (gamma 2.0 vs 3.2 at the 91-day setting with volatility 40% vs 25%).

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Previous: [[concepts/09-risk-measurement-ii/speed-color-and-zomma]]
- Next: [[concepts/09-risk-measurement-ii/lambda-leverage]]
- Built on: [[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]], [[concepts/08-dynamic-hedging/rehedging-frequency-and-costs]]
- See also: [[glossary]], [[formulas]]
