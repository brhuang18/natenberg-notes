# Theta in different conditions

**One-line definition:** an option's time decay (theta) is largest in size at the money; as expiration nears it grows without limit for an at-the-money option but fades to nothing for in- and out-of-the-money options; and, ignoring interest, at-the-money theta is directly proportional to volatility.

## Intuition
Theta is the rate at which **time value** melts away ([[concepts/07-risk-measurement-i/theta]]). So ask: *when is there the most time value to lose, and how quickly does it go?*
- Deep in the money or far out of the money, an option has almost no time value ([[concepts/03-contract-specifications-and-option-terminology/intrinsic-value-and-time-value]]). Nothing to lose, so theta is tiny.
- At the money, the option is *all* time value. Theta is largest here.

Think of an ice cube melting. A big cube melts a little each minute. As it shrinks, each minute removes a larger *share* of what is left, and in the last minute the whole thing vanishes. An at-the-money option behaves like that cube; an in-the-money or out-of-the-money option is an ice cube that is almost gone already.

*(The book plots theta as an absolute value, even though it is usually quoted as a negative number for a long option. We do the same in the figure.)*

## The maths and the four patterns
![Theta against underlying price, time and volatility](../../images/ch09-theta-profiles.png)

**1. As the underlying price changes (Figure 9-8).** Theta forms a hump centred on the exercise price. It is largest at the money and small far in or out. A higher exercise price gives a **bigger** hump (the right-hand curve in the left panel). Reason: consider an at-the-money call struck at 10 and one struck at 1,000, same time and volatility. The 1,000 call is a right to buy something much more valuable, so it is worth much more, and all of that value is time value. In fact value and theta are **proportional to the exercise price**: the 1,000 call is worth exactly 100 times the 10 call, and its theta is exactly 100 times greater ([[concepts/09-risk-measurement-ii/at-the-money-scaling-with-the-exercise-price]]).

**2. As time passes (Figures 9-9 and 9-10).** Underlying 100, volatility 25%, theta per day (negative means value lost):

| Days left | 90 call (in the money) | 100 call (at the money) | 110 call (out of the money) |
|---|---|---|---|
| 180 | $-0.0154$ | $-0.0194$ | $-0.0175$ |
| 90 | $-0.0182$ | $-0.0275$ | $-0.0214$ |
| 30 | $-0.0153$ | $-0.0476$ | $-0.0206$ |
| 15 | $-0.0074$ | $-0.0674$ | $-0.0121$ |
| 7 | $-0.0009$ | $-0.0986$ | $-0.0023$ |
| 3 | $0.0000$ | $-0.1507$ | $0.0000$ |
| 1 | $0.0000$ | $-0.2610$ | $0.0000$ |

Early in life the three decay at similar rates. Late in life the in- and out-of-the-money options **slow down to nothing** while the at-the-money option **accelerates**, in theory without limit at the moment of expiration. (In- and out-of-the-money lines are not exactly the same; the book draws one line for both.)

**3. As volatility changes (Figure 9-11).** With zero volatility the underlying cannot move, there is no time premium and so theta is zero (ignoring interest). Raising volatility raises time premium and therefore theta. For the at-the-money option the relationship is a straight line: **theta is proportional to volatility**. At 91 days: volatility 10% gives $-0.0109$, 20% gives $-0.0219$, 40% gives $-0.0436$. Exactly double and quadruple. For in- and out-of-the-money options the line curves, and theta may reach zero well before volatility does (the 110 call at 10% volatility has a theta of only $-0.002$).

**4. A higher vs a lower exercise price, equally far from the underlying (Figure 9-11).** The 110 option has a **greater** theta than the 90 option, and the gap grows with volatility:

| Volatility | theta 110 | theta 90 | value of 110 call | value of 90 put |
|---|---|---|---|---|
| 20% | $-0.0145$ | $-0.0119$ | 0.95 | 0.71 |
| 30% | $-0.0280$ | $-0.0243$ | 2.49 | 2.02 |
| 40% | $-0.0408$ | $-0.0360$ | 4.28 | 3.58 |

The reason (a point first made in Chapter 6): two options equally far out of the money, an out-of-the-money **call** at 110 and an out-of-the-money **put** at 90, are *not* worth the same under a lognormal distribution. The call (higher exercise price) carries more time premium. If the underlying does not move, the option with more time premium has more to lose, so it must decay faster. (Without interest, a call and a put with the same exercise price share the same theta, so comparing "110" with "90" is the same as comparing the out-of-the-money call with the out-of-the-money put.)

## Worked example
**How fast does the at-the-money option decay in its last month?** Underlying 100, volatility 25%. With 30 days left the 100 call is worth 2.86 and decays $0.0476$ a day. With 7 days left it is worth 1.38 and decays $0.0986$ a day: double the daily rate on half the days. With 1 day left it is worth 0.52 and "decays" $0.26$ a day, and the day after that it expires (worth 0 if the underlying is exactly 100). The fraction of the *remaining* value lost per day goes: $0.0476/2.86 = 1.7\%$ with 30 days left; $0.0986/1.38 = 7.1\%$ with 7 days left; $0.261/0.522 = 50\%$ with 1 day left.

## Common confusions
- **Not "decays fastest in the last month for every option".** Only at-the-money options accelerate. Out-of-the-money options that look cheap lose almost nothing per day close to expiration, because there is nothing left to lose (the option is worth about zero and is either going to expire worthless or move into the money).
- **Higher underlying price does not always mean higher theta.** It does for **at-the-money** comparisons (a 1,000 call vs a 10 call). For one option, as the underlying moves away from its strike, theta falls.
- **Our figures assume no interest.** With interest the call and put at one strike have different thetas ([[concepts/07-risk-measurement-i/theta]]). The patterns above still hold.

## Related
- Chapter: [[chapters/09-risk-measurement-ii]]
- Maths needed: [[00-maths-refresher/proportionality-and-percentage-change]]
- Previous: [[concepts/09-risk-measurement-ii/vanna-and-charm]]
- Next: [[concepts/09-risk-measurement-ii/estimating-atm-theta-with-the-square-root-of-time]]
- See also: [[concepts/06-volatility/lognormal-distributions]], [[concepts/07-risk-measurement-i/gamma-and-theta-trade-off]], [[glossary]], [[formulas]]
